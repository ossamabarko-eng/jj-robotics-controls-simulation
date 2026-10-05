# Robotic Arm Controls: Diagnostics and Design Optimization

Two-part engineering exercise from the **Johnson & Johnson MedTech Robotics & Controls virtual experience** (Forage). The scenario: a surgical robotic arm shows delayed control responses, and I diagnose the delay, then propose and test design changes.

> **Please note:** the Forage materials are an educational simulation, not real Johnson & Johnson systems or data. The "optimizations" below are simulated with simple formulas; I state this limit in the reports and do not claim real-world performance gains.

## Task 1: Control system diagnostics
**Notebook:** [`task1-control-diagnostics/Control_System_Diagnostic_Notebook.ipynb`](task1-control-diagnostics/Control_System_Diagnostic_Notebook.ipynb)

I timed three arm commands (`move_arm`, `rotate_joint`, `adjust_grip`) with Python, compared them with their expected response times, wrote a hypothesis, and tested a simulated 20% improvement.

| Command | Observed (s) | Expected (s) | Finding |
|---|---|---|---|
| move_arm | 0.102 | 0.10 | About 2 ms over target |
| rotate_joint | 0.15 | 0.18 | Slowest command, but within its limit |
| adjust_grip | 0.051 | 0.09 | Well within its limit |

Report: [`reports/Diagnostic_Report.pdf`](reports/Diagnostic_Report.pdf)

## Task 2: Design optimization proposal
**Notebook:** [`task2-design-optimization/Robotic_Arm_Design_Simulation.ipynb`](task2-design-optimization/Robotic_Arm_Design_Simulation.ipynb)

I identified two issues, **actuator strain** and **sensor misalignment**, and proposed a fix for each:

1. Upgrade the shoulder, elbow and wrist actuators (15% efficiency target).
2. Realign and reinforce the sensor mounts, with a start-up calibration check (10% reinforcement target).

I tested the factors iteratively with NumPy (three trials, with acceptance criteria I defined) and validated the chosen values against the expected response times from Task 1.

| Metric | Before | After |
|---|---|---|
| Response time (simulated) | 0.20 s | 0.17 s (-15%) |
| Durability score (simulated) | 75 | 82.5 (+10%) |
| Commands within expected time | 2 of 3 | 3 of 3 |

Proposal: [`reports/Design_Optimization_Proposal.pdf`](reports/Design_Optimization_Proposal.pdf) (Word version included)

Annotated CAD visuals are in [`task2-design-optimization/images/`](task2-design-optimization/images/).

## Skills shown
Python (NumPy, Matplotlib), Jupyter, performance measurement and diagnostics, iterative testing, simulation-based validation, technical writing, design annotation.

## Run it yourself
```bash
pip install numpy matplotlib notebook
jupyter notebook
```
Open either notebook and run the cells from top to bottom. Timings vary slightly between machines. The Task 2 notebook asks for two inputs; I used `0.15` and `0.10`.

## Credits
Starter notebooks and templates come from the Forage / Johnson & Johnson MedTech program (<https://github.com/Forage-Simulations/Johnson-Johnson-Robotics-Controls>). The analysis, filled-in notebooks, iterative tests, annotations and written reports are my own work.
