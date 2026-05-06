# RISC-V 32-Bit Single-Cycle CPU
![Status](https://img.shields.io/badge/Status-In--Progress-orange) 
![Architecture](https://img.shields.io/badge/ISA-RV32I-blue)
![Tools](https://img.shields.io/badge/Tools-Logisim-green)

## 📌 Overview
This repository contains the hardware design and implementation of a single-cycle processor based on the **RV32I Instruction Set Architecture (ISA)**. This project, completed for the CSC 364 Computer Architecture course at Louisiana Tech University, demonstrates a modular approach to CPU design, including custom ALU logic, register file management, and integrated data memory pathways.

---

## 📂 Directory Structure

| Folder | Content |
| :--- | :--- |
| 📁 `documentation/` | **Technical Design Reports** (ALU and Register File specifications) |
| 📁 `hardware/` | **Logisim Circuit Files** (`.circ`) including the main CPU and sub-modules |
| 📁 `tests/` | **Verification Programs** (Hexadecimal machine code for Program A, B, and C) |

---

## 🛠️ Implementation Roadmap (CSC 364 Tasks)

### **✅ Completed: Datapath & Core Modules**
* **32-Bit ALU:** Fully implemented and validated for arithmetic and logical operations (ADD, SUB, AND, OR, XOR, SLT) per **Table 6** of the project specifications.
* **Integrated Data Path:** Engineered a unified interface between the **32x32-bit Register File** and **Data Memory**. This ensures synchronous write-back and streamlined Load/Store execution.
* **Field Decoding:** Implemented hardware slicing for the instruction bus to extract Opcode, rd, rs1, rs2, funct3, and funct7 fields.

### **🏗️ In Progress: Control & Logic**
* **Main Control Unit:** Designing the logic to generate the 10+ concurrent control signals (RegWrite, ALUSrc, MemRead, MemWrite, etc.) required for the single-cycle execution of RV32I.
* **Immediate Generator (ImmGen):** Constructing the sign-extension and reconstruction logic for I, S, B, and J formats.
* **PC Update Logic:** Building the multiplexer system to handle sequential execution (PC+4) alongside PC-relative branches and jumps.

> [!IMPORTANT]
> ### **Upcoming Milestone: End-to-End Validation**
> The final phase involves executing the three mandatory test programs (A, B, and C) to verify register write-back, memory alignment, and branch decision logic accuracy.

---

## 🔬 Architectural Highlights

> ### **Optimized Memory Interface**
> This design utilizes an integrated Register-Memory block. By sharing a common bus architecture, the design minimizes propagation delay for `lw` and `sw` instructions, ensuring the datapath remains stable within a single clock cycle.

### **Supported Instruction Subset**
The processor is architected to support the following classes as defined in the **RV32I Instruction Set**:
* **R-type:** `add`, `sub`, `and`, `or`, `xor`, `slt`
* **I-type:** `addi`, `slti`, `andi`, `ori`, `xori`, `lw`
* **S-type:** `sw`
* **B-type:** `beq`, `bne`
* **J-type:** `jal`

---

## 📝 How to Use
1. **Prerequisites:** A compatible version of **Logisim** is included in the `/tools` directory. Download and run this file to ensure the `.circ` libraries load correctly.
2. **Clone the Repo:** ```bash
   git clone [https://github.com/your-username/ProcessorDesign.git](https://github.com/your-username/ProcessorDesign.git)
