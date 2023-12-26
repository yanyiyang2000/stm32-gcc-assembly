## Table of Contents
- [Prerequisites](#prerequisites)
- [Setting Project Name](#setting-project-name)
- [Building](#building)
- [Flashing](#flashing)
- [Cleaning](#cleaning)
- [Tools](#tools)

## Prerequisites
Install the following packages:
- `gcc-arm-none-eabi`
- `gdb-multiarch`
- `openocd`

## Setting Project Name
In the project root directory, modify the following entry in `CMakeLists.txt`:
```cmake
project(
    <PROJECT_NAME>
    LANGUAGES C ASM
)
```

## Building
In the project root directory, use the following commands one by one:
```bash
cmake -B build
cmake --build build
```

## Flashing
In the `build` directory, use the following command:
```bash
openocd -f interface/stlink.cfg -f target/stm32l4x.cfg -c "program <PROJECT_NAME>.elf verify reset exit"
```

## Cleaning
In the `build` directory, use the following command:
```bash
rm -rf *
```

## Tools
In the `build` directory, use the following command to view the dieassembly code:
```bash
arm-none-eabi-objdump -d -s <PROJECT_NAME>.elf
```

In the `build` directory, use the following command to view the output information:
```bash
arm-none-eabi-readelf -S <PROJECT_NAME>.elf
```