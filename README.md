# led-matrix-rs-template

This template provides you with all the boilerplate necessary to program the [LED-matrix](https://github.com/InES-HPMM/LED-Matrix-Workshop/tree/main) with Rust.
The library [`led-matrix-rs`](https://github.zhaw.ch/senk/led-matrix-rs) provides a user-friendly API to do so.
It even gives you a GUI emulator for free, so you can debug your application logic with ease.
Its documentation can be found [here](https://github.zhaw.ch/pages/senk/led-matrix-rs/led_matrix/).

> [!IMPORTANT]
> **Please make sure you go through all setup steps throroughly!**

## Setup

1. Install the Rust toolchain.
   The official installation instructions can be found [here](https://www.rust-lang.org/tools/install).
   
   **DO NOT** install the Rust compiler via a system package manager.
   These compilers are intended for building the packages of the distribution.
   For development, the official toolchain manager `rustup` is the recommended way to install a compiler.
   Most Linux distributions ship an official `rustup` package, which is perfectly fine to use.
   
1. Add the cross-compilation target for the Raspberry Pi Pico:
   ```sh
   rustup target add thumbv6m-none-eabi
   ```

1. Install `elf2uf2`, which is necessary to convert the firmware to a flashable format:
   ```sh
   cargo install elf2uf2-rs
   ```
1. If you are on linux, you need a couple dependencies from your package manager to run the GUI emulator.
   Refer to the documentation [here](https://github.com/emilk/egui?tab=readme-ov-file#demo), it should only be a single command.

   If you can't get the GUI emulator working for some reason, there is also a simpler TUI emulator.
   You can use it by adding `--features tui` to any cargo command you use for running your code.
   However, be aware that the TUI emulator has a worse user experience.
   The terminal cannot detect key release events, so you must press e separate button to indicate when the joystick was released.

## Usage

Run your application in the emulator:

```sh
cargo run
```

To run on the hardware, first connect the LED-matrix while keeping BOOTSEL pressed, then:

```sh
cargo run --release --target thumbv6m-none-eabi
```
