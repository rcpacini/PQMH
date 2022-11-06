# PQMH
Packed Queued Message Handler written in LabVIEW

# Overview

LabVIEW framework to build and deploy applications using
Packed Project Libraries (PPLs).

# Getting Started

- Install LabVIEW 2022 (or later)
  - (optional) Install NI DSC Module with a Debug/Deploy License to debug in Run-Time Engine
- Run Main.exe
  - Create a Startup.ini file next to Main.exe to define the applications to load

![Main](/Support/Screenshots/Main.png)


# Startup.ini

The startup.ini configuration file defines one or more applications to load (does not launch).
Each application must have a separate configuration file to load the "\[app]" section
and "vi" key to the qualified VI name. The packed library must be located in a sub-directory
to the startup.ini.

```
; startup.ini
[apps]
; APP_NAME = CONFIG_PATH
DEMO = .\startup.ini

[app]
; vi = QUALIFIED_VI_NAME as *.lvlibp:*.vi or *.lvlib:*.vi
vi = Demo.lvlib:Demo.vi
; vi = Demo.lvlibp:Demo.vi

```

# Objective

Streamline large application development by:
- Simplifying the LabVIEW development, debugging and deployment workflow
- Minimal core framework libraries to support a module heirarchy design pattern
- Execute multiple applications simultaneously
- Minimal configuration management with run-time reconfigurability

# Can & Cannots

- Cannot use functional globals since PPLs embed support libraries
  - Fix: Use named single element queues since they share the same namespace
- Can debug in development environment (or with NI DSC Module Debug/Deploy license)
