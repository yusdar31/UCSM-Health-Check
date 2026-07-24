# Cisco UCS Health Check

> Automated Cisco UCS Manager Health Check & Inventory Report using PowerShell and Cisco UCS PowerTool.

![PowerShell](https://img.shields.io/badge/PowerShell-5.1+-5391FE?logo=powershell)
![Cisco UCS](https://img.shields.io/badge/Cisco-UCS-success)
![Platform](https://img.shields.io/badge/Platform-Windows-blue)
![License](https://img.shields.io/badge/License-MIT-green)

---

## Overview

Cisco UCS Health Check is a PowerShell-based reporting tool that collects inventory and health information directly from **Cisco UCS Manager** using **Cisco UCS PowerTool**.

The script automatically generates an HTML health report together with CSV exports for inventory, firmware, power, ports, licenses, and faults.

The project was designed to simplify:

- Annual Shutdown Validation
- Health Check
- Inventory Documentation
- Firmware Audit
- Capacity Review
- Operational Documentation

---

## Features

### Executive Summary

- UCS Domain
- UCS Manager Version
- Health Score
- Fabric Interconnect Count
- Chassis Count
- Blade Count
- Active Fault Count

---

### Fabric Interconnect

- Fabric ID
- Cluster Role
- Model
- Serial Number
- Management IP
- System Firmware
- Kernel Firmware
- Port Usage
- License Summary
- Thermal Status
- Operability

---

### Chassis

- Chassis ID
- Model
- Serial Number
- Power Status
- Thermal Status
- PSU Count
- PSU Redundancy
- Slot Usage

---

### IO Module

- Fabric
- Model
- Serial
- Running Firmware
- Backup Firmware
- Operability

---

### Blade Server

- Chassis
- Slot
- Model
- Serial Number
- Service Profile
- CPU
- Core Count
- Memory
- CIMC Firmware
- Power Status
- Thermal
- Operability

---

### Power Statistics

- Current Power
- Average Power
- Maximum Power
- Voltage
- Current

---

### Active Fault

- Severity
- Fault Code
- Description
- Affected Object
- Created Time

---

### Service Profile

- Assigned Blade
- Association State
- Organization
- Template Type

---

### Firmware Inventory

- Fabric Firmware
- Kernel Firmware
- CIMC Firmware
- IOM Firmware

---

### License Summary

- License Features
- License Lines

---

### Export

✔ HTML Report

✔ CSV Export

✔ Raw CSV for Troubleshooting

---

## Example Report

```
Cisco UCS Health Check Report

Executive Summary

Health Score        : 92/100
Fabric Interconnect : 2
Chassis             : 5
Blade Servers       : 18
Faults              : 2 Minor
```

---

## Requirements

### Operating System

Windows

### PowerShell

PowerShell 5.1 or newer

### Cisco UCS Manager

Tested with

```
Cisco UCS Manager 4.3(6f)
```

### Cisco UCS PowerTool

Tested with

```
Cisco.UCSManager 3.0.6.21
```

---

## Installation

Clone repository

```powershell
git clone https://github.com/<username>/UCSHealthCheck.git
```

Go to repository

```powershell
cd UCSHealthCheck
```

Allow PowerShell execution

```powershell
Set-ExecutionPolicy -Scope Process Bypass
```

Verify UCS PowerTool

```powershell
Get-Module Cisco.UCSManager -ListAvailable
```

---

## Usage

Standard

```powershell
.\Generate-UCSHealthCheck.ps1 `
-UcsIp "10.222.16.198"
```

Complete

```powershell
.\Generate-UCSHealthCheck.ps1 `
-UcsIp "10.222.16.198" `
-PrimaryFabric A `
-OutputDirectory "C:\UCS-Report" `
-IncludeRawCsv `
-OpenReport
```

---

## Parameters

| Parameter | Description |
|------------|-------------|
| UcsIp | UCS Manager Virtual IP |
| PrimaryFabric | Primary Fabric (A/B) |
| OutputDirectory | Report Output Folder |
| IncludeRawCsv | Export Raw Inventory |
| OpenReport | Open HTML automatically |

---

## Output

Generated files

```
Output/

UCS-Health-Check.html

FabricInterconnect.csv

Chassis.csv

Servers.csv

Firmware.csv

Faults.csv

Licenses.csv

ServiceProfiles.csv

ServerPower.csv

PSUInventory.csv

RawFabricPorts.csv

RawServerPorts.csv

RawUplinkPorts.csv

RawFcPorts.csv

RawAppliancePorts.csv
```

---

## Project Structure

```
UCSHealthCheck

├── Generate-UCSHealthCheck.ps1

├── README.md

├── LICENSE

├── CHANGELOG.md

├── docs

│   ├── Installation.md

│   ├── UserGuide.md

│   ├── Troubleshooting.md

│   └── AnnualShutdown.md

├── templates

│   └── report.css

├── examples

│   └── Run.ps1

└── sample-output

    ├── report.html

    └── csv
```

---

## Annual Shutdown Workflow

### Before Shutdown

- Run Health Check
- Export Inventory
- Export Raw CSV
- Save UCS Backup
- Save Tech Support Bundle

### After Startup

- Run Health Check again
- Compare Inventory
- Verify Fault Status
- Verify Firmware
- Verify Service Profile
- Verify Blade Status

---

## Troubleshooting

### Duplicate Inventory

Run

```powershell
Get-UcsPSSession
```

Disconnect existing sessions

```powershell
Disconnect-Ucs
```

---

### Cannot Connect

Check

- IP Address
- HTTPS Port
- Username
- Password
- Firewall

---

### Script Blocked

```powershell
Set-ExecutionPolicy -Scope Process Bypass
```

---

## Roadmap

- [x] HTML Report
- [x] CSV Export
- [x] Inventory Collection
- [x] Health Score
- [x] License Report
- [x] Power Statistics

Future

- [ ] PDF Export
- [ ] Excel Export
- [ ] Email Report
- [ ] Health Trend
- [ ] Grafana Integration
- [ ] Intersight Support

---

## Tested Environment

| Component | Version |
|------------|---------|
| Cisco UCS Manager | 4.3(6f) |
| Cisco UCS PowerTool | 3.0.6.21 |
| Windows PowerShell | 5.1 |
| Windows | Windows Server / Windows 10 / Windows 11 |

---

## Contributing

Contributions are welcome.

If you find a bug or have an enhancement idea, feel free to open an Issue or submit a Pull Request.

---

## License

MIT License

---

## Author

Developed for Cisco UCS operational health checking and inventory reporting using Cisco UCS PowerTool.
