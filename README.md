# Final-Task-RoboManipal
This repository includes all the files and folder related to the implementation task
# Flexible Joint Robot Models

This folder contains the Simulink files used for comparing different control methods for a flexible joint robot.

The main idea is to see how different controllers affect:

- tracking of the reference input
- oscillations in the output
- smoothness of the torque signal

The output is mainly checked using:
- **TrackingScope**
- **TorqueScope**

---

## Files

### `FJR_Baseline.slx`
This is the basic flexible joint robot model.

It is mainly the plant model and is used as the starting system before applying the different controllers.

---

### `FJR_Classical_SMC.slx`
This file contains the flexible joint robot with **classical sliding mode control**.

In this model:
- the output is made to follow the reference input
- the controller uses switching control
- the torque changes sharply

From the plots:
- tracking is present
- but there are clear oscillations
- torque has strong chattering

So this file is mainly used to show the normal behavior of classical SMC.

---

### `FJR_Saturation_SMC.slx`
This file contains the model with **saturation-based sliding mode control**.

In this model:
- the switching part of the controller is softened using a saturation function
- this is done to reduce chattering

From the plots:
- torque becomes smoother than classical SMC
- tracking is still oscillatory, but less harsh

This file is used to compare how much improvement happens when the switching is smoothed.



### `FJR_VBSMC.slx`
This file contains the model with **Variable Boundary Sliding Mode Control (VBSMC)**.

In this model:
- the boundary layer is not fixed
- the controller response changes depending on the error

From the plots:
- torque is smoother than classical SMC
- output response is more controlled
- oscillations are still present but better managed

This file is used to study a smoother and more adaptive version of SMC.

---

## What is being compared

The main comparison between the models is based on:

- how well the system tracks the input
- how much oscillation is present
- how smooth the torque signal is

---

## General observation

- **Classical SMC** gives strong control but high chattering
- **Saturation SMC** reduces chattering
- **VBSMC** gives a smoother response and better balance

---

## How to run

1. Open any `.slx` file in Simulink
2. Run the simulation
3. Open the scopes
4. Compare the tracking and torque plots
