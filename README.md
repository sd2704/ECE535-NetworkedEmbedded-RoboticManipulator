# ECE535-NetworkedEmbedded-RoboticManipulator
Course Project for ECE 535 Networked Embedded Systems - Robotic Manipulator with Visual Language Action Models (VLA's)
Team Members: Sean DiMattio, April Ramsey 

## Motivation
Vision-Language-Action models let people control robots with natural language instead of
hand-coded trajectories. But models like OpenVLA have 7B parameters, which makes them hard to run on 
hardware with limited memory. This project explores compressing a VLA to fit within 16GB
and running it on a simulated arm.

## Design Goals
- Run OpenVLA inference on a simulated robotic arm from language instructions
- Compress the 7B model to fit within a 16GB memory budget
- Evaluate the tradeoff between compression level, memory, latency, and task success

## Deliverables
1. Summary of how VLA models work 
2. Compressed OpenVLA model running within 16GB
3. Pick-and-place environment in Isaac Sim integrated with the compressed model
4. Evaluation of success rate, memory, and latency across compression levels

## System Blocks
Language instruction + camera image 
        ↓
Compressed OpenVLA 
        ↓
Action tokens → end-effector deltas + gripper command
        ↓
IK / arm controller
        ↓
Simulated arm moves in Isaac Sim → new camera image

## Hardware / Software Requirements
**Hardware:** NVIDIA RTX GPU with at least 16GB VRAM
**Software:** Ubuntu 22.04, NVIDIA Isaac Sim, Python, PyTorch, Hugging Face Transformers,
bitsandbytes, OpenVLA

## Team Responsibilities & Lead Roles
| Member | Responsibilities |
| Sean DiMattio | Isaac Sim environment, controller integration, model-to-simulator interface | Setup, Software, Networking |
| April  | OpenVLA setup, model compression, benchmarking | Research, Algorithm Design, Writing |

## Project Timeline

## References
1. Kim et al., "OpenVLA: An Open-Source Vision-Language-Action Model." https://arxiv.org/abs/2406.09246
2. Song et al., "Rethinking the Practicality of Vision-language-action Model: A Comprehensive Benchmark and An Improved Baseline." https://arxiv.org/abs/2602.22663 · Code: https://github.com/OpenHelix-Team/LLaVA-VLA
3. NVIDIA, "Training Healthcare Robots from Scratch with Isaac for Healthcare." https://docs.nvidia.com/learning/physical-ai/getting-started-with-isaac-for-healthcare/latest/index.html
4. NVIDIA Isaac Sim. https://github.com/isaac-sim/IsaacSim
