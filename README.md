# README

## Table of contents

<!--toc:start-->
- [Summary](#summary)
- [Installation](#installation)
- [Usage](#usage)
- [License](#license)
- [Troubleshooting](#troubleshooting)
<!--toc:end-->

## Summary

`trayicon` is a simple program that displays an icon in the system tray for a
given command. The icon can be used to restart or quit the command. It is also
possible to set a custom icon for the command.

The demo below shows an example where the program [kmonad](https://github.com/kmonad/kmonad/releases/latest)
is executed with the corresponding icon on Windows.
![demo](https://media.githubusercontent.com/media/BartSte/trayicon/refs/heads/develop/examples/windows/kmonad/trayicon-kmonad.gif)

## Installation

### Precompiled

You can install `trayicon` by downloading the precompiled binaries from the
[latest github release](https://github.com/BartSte/trayicon/releases/latest).
For windows, a standalone executable is provided. For linux, a tarball is
provided that contains an executable and required system libraries. A bash
script is used to start the program. MacOS is not supported at the moment.

### From source

Building from source is straightforward as the only dependency is `Qt6`. A
`setup` script is provided that installs Qt6 for you. You need to make sure that
you set an environment variable `QT_INSTALLER_JWT_TOKEN` with a valid token
as is explained in the [Qt documentation](https://doc.qt.io/qt-6/get-and-install-qt-cli.html).
The detailed steps are provided below. MacOS is not supported at the moment.

#### Linux

To build against Qt6 system libraries, you need to install the Qt6 developement
environment and ninja build.
- On Fedora:
sudo dnf install qt6-qtbase-devel qt6-qtwayland-devel ninja-build

-On Ubuntu
sudo sudo apt install qt6-base-dev qt6-wayland-dev ninja-build

Then create a build directory, move to it and build
```
mkdir build
cd build
cmake -G "Ninja" -S "../" -B "./" -DCMAKE_BUILD_TYPE="shared" -DCMAKE_BUILD_WITH_INSTALL_RPATH=on
ninja
```

#### Windows

- Tested on Windows 11, with MSVC 2022.

- Run the `.\scripts\setup.ps1` script to install Qt6. You can choose to
  install the `--static` Qt libraries (default) if you want to build a
  standalone executable, or the `--shared` libraries if you want use dynamic
  linking. The latter is faster, as it just downloads the libraries, instead of
  building them from source.

- Run the `.\scripts\configure.ps1` script to configure the build.

- Run the `cmake --build build --config Release` command to build the program
  and create an executable.

## Usage

Run the `trayicon` program as follows:

```sh
trayicon [options] -- "command"
```

For example:

```sh
trayicon --icon /path/to/icon.png -- "my_command --option=value arg1"
```

This will start the `my_command --option=value arg1` command and display an
icon in the system tray.

For more information, run:

```sh
trayicon --help
```

## License

This project is licensed under the MIT License - see the [LICENSE](./LICENSE)
file for details.

## Troubleshooting

If you encounter any issues, please report them on the issue tracker at:
[trayicon issues](https://github.com/BartSte/trayicon/issues)
