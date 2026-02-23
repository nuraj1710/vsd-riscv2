# Task-1: Environment Setup & RISC-V Reference Bring-Up — Submission

## Environment Used
 GitHub Codespace only

---

## Step 1: GitHub Codespace Setup

- Forked the repository: `https://github.com/vsdip/vsd-riscv2`
- Launched GitHub Codespace from the forked repository
- Codespace built successfully and opened without errors

---

## Step 2: Toolchain Verification

Ran the following commands to verify all tools are installed:

```bash
riscv64-unknown-elf-gcc --version
spike --version
iverilog -V
```

**Output:**
- `riscv64-unknown-elf-gcc (SiFive GCC 8.3.0-2019.08.0) 8.3.0` 
- `spike` is installed and functional 
- `Icarus Verilog version 11.0 (stable)` 

---

## Step 3: RISC-V Reference Program Execution

### Commands Used:
```bash
cd samples
riscv64-unknown-elf-gcc -o sum1ton.o sum1ton.c
spike pk sum1ton.o
```

### Output:
```
bbl loader
Sum from 1 to 9 is 45
```

### Screenshots![5](https://github.com/user-attachments/assets/0369c96d-af44-42b2-a3cb-da58b97b74b3)
:
> 📸 **
![0](https://github.com/user-attachments/assets/de080135-07bb-4aaf-a825-b8b795b1a077)
[1](https://github.com/user-attachments/assets/54eb65cb-9f58-49b0-8f1c-867771063c13)
![2](https://github.com/user-attachments/assets/bfbb99ab-f216-45c1-ad34-daeb7e2ff0a1)
![3](https://github.com/user-attachments/assets/f031c807-701d-4a43-a0ae-07833dd5f403)
![4](https://github.com/user-attachments/assets/a0f6b34a-a0d9-4e1c-82d3-56ff6826fd47)

RISC-V program compiled and ran successfully using Spike simulator.

---

## Step 4: VSDFPGA Labs Execution

### Commands Used:
```bash
cd /workspaces/vsd-riscv2
git clone https://github.com/vsdip/vsdfpga_labs.git
cd vsdfpga_labs
```

### Screenshot:
> 📸 **![5](https://github.com/user-attachments/assets/121dc6c5-2e9c-4380-bb01-f93d2ec61698)]**

VSDFPGA labs cloned and executed successfully inside the same Codespace.

---

## Understanding Check — Answers

### Q1. Where is the RISC-V program located in the vsd-riscv2 repository?

The RISC-V programs are located in the `samples/` folder of the repository. The main program is `sum1ton.c`, along with a custom version `1ton_custom.c`, an assembly file `load.S`, and a `Makefile`.

---

### Q2. How is the program compiled and loaded into memory?

The program is compiled using `riscv64-unknown-elf-gcc`, which is a cross-compiler that converts C source code into a RISC-V 64-bit ELF binary. The compiled binary is then loaded into memory by the **Spike RISC-V ISA simulator** using the **proxy kernel (`pk`)**, which acts as a minimal operating system — it sets up the memory layout and loads the ELF binary before handing execution to the RISC-V core.

---

### Q3. How does the RISC-V core access memory and memory-mapped IO?

The RISC-V core accesses memory using **load and store instructions** . For memory-mapped IO, specific physical address ranges are assigned to hardware peripherals (like UART, GPIO, timers). When the core reads or writes to those addresses, it communicates directly with the hardware peripheral instead of RAM — this is the standard memory-mapped IO (MMIO) model used in embedded and SoC designs.

---

### Q4. Where would a new FPGA IP block logically integrate in this system?

A new FPGA IP block would integrate as a **memory-mapped peripheral** on the system bus. It would be assigned a dedicated address range in the memory map, so the RISC-V core can communicate with it using standard load/store instructions. 

---

## Optional Confidence Task

Modified the constant `n=9` in `sum1ton.c` to `n=15` and recompiled:

```bash
riscv64-unknown-elf-gcc -o sum1ton.o sum1ton.c
spike pk sum1ton.o
```

**Changed Output:**
```
Sum from 1 to 15 is 120
```

> 📸 **[Insert screenshot of changed output]**

Successfully modified, rebuilt, and observed the updated output.

---

## Summary!







| Task | Status |
|------|--------|
| GitHub Codespace Setup | ✅ Done |
| Toolchain Verification | ✅ Done |
| RISC-V Program Execution | ✅ Done |
| VSDFPGA Labs Cloned & Run | ✅ Done |
| Understanding Questions Answered | ✅ Done |
| Optional Confidence Task | ✅ Done |
