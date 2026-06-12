---
title: "Nvidia GeForce GTX 560 M not recognized as an OpenCL platform by 5.15.0-50 kernel"
date: 2022-10-16
forum: MINT
---

### Post by mikenavy on 2022-10-16
Hi,

I use Linux Mint 20.3 Mate, based on Ubuntu 20.04 LTS.

Before to update to Linux Mint 21, based on Ubuntu 22.04 LTS, I have tried 5.15.0-50 kernel with HWE. This was intended as a test of my hardware compatibility with the hardware stack of Ubuntu 22.04, before a possible update.

At a first glance, all seemed OK; nut I noticed that LibreOffice was unable to use OpenCL. A simple "clinfo" command confirmed this:

```
$ clinfo
Number of platforms                               0
```

I went back from 5.15.0-50 kernel to 5.4.0-128 one. Now, "clinfo" output is:
```

$ clinfo
Number of platforms                               1
  Platform Name                                   NVIDIA CUDA
  Platform Vendor                                 NVIDIA Corporation
  Platform Version                                OpenCL 1.2 CUDA 9.1.84
  Platform Profile                                FULL_PROFILE
  Platform Extensions                             cl_khr_global_int32_base_atomics cl_khr_global_int32_extended_atomics cl_khr_local_int32_base_atomics cl_khr_local_int32_extended_atomics cl_khr_fp64 cl_khr_byte_addressable_store cl_khr_icd cl_khr_gl_sharing cl_nv_compiler_options cl_nv_device_attribute_query cl_nv_pragma_unroll cl_nv_copy_opts cl_nv_create_buffer
  Platform Extensions function suffix             NV


  Platform Name                                   NVIDIA CUDA
Number of devices                                 1
  Device Name                                     GeForce GTX 560M
  Device Vendor                                   NVIDIA Corporation
  Device Vendor ID                                0x10de
  Device Version                                  OpenCL 1.1 CUDA
  Driver Version                                  390.154
  Device OpenCL C Version                         OpenCL C 1.1 
  Device Type                                     GPU
  Device Topology (NV)                            PCI-E, 01:00.0
  Device Profile                                  FULL_PROFILE
  Device Available                                Yes
  Compiler Available                              Yes
  Max compute units                               4
  Max clock frequency                             1550MHz
  Compute Capability (NV)                         2.1
  Max work item dimensions                        3
  Max work item sizes                             1024x1024x64
  Max work group size                             1024
  Preferred work group size multiple              32
  Warp size (NV)                                  32
  Preferred / native vector sizes                 
    char                                                 1 / 1       
    short                                                1 / 1       
    int                                                  1 / 1       
    long                                                 1 / 1       
    half                                                 0 / 0        (n/a)
    float                                                1 / 1       
    double                                               1 / 1        (cl_khr_fp64)
  Half-precision Floating-point support           (n/a)
  Single-precision Floating-point support         (core)
    Denormals                                     Yes
    Infinity and NANs                             Yes
    Round to nearest                              Yes
    Round to zero                                 Yes
    Round to infinity                             Yes
    IEEE754-2008 fused multiply-add               Yes
    Support is emulated in software               No
    Correctly-rounded divide and sqrt operations  No
  Double-precision Floating-point support         (cl_khr_fp64)
    Denormals                                     Yes
    Infinity and NANs                             Yes
    Round to nearest                              Yes
    Round to zero                                 Yes
    Round to infinity                             Yes
    IEEE754-2008 fused multiply-add               Yes
    Support is emulated in software               No
  Address bits                                    64, Little-Endian
  Global memory size                              3150839808 (2.934GiB)
  Error Correction support                        No
  Max memory allocation                           787709952 (751.2MiB)
  Unified memory for Host and Device              No
  Integrated memory (NV)                          No
  Minimum alignment for any data type             128 bytes
  Alignment of base address                       4096 bits (512 bytes)
  Global Memory cache type                        Read/Write
  Global Memory cache size                        65536 (64KiB)
  Global Memory cache line size                   128 bytes
  Image support                                   Yes
    Max number of samplers per kernel             16
    Max 2D image size                             16384x16384 pixels
    Max 3D image size                             2048x2048x2048 pixels
    Max number of read image args                 128
    Max number of write image args                8
  Local memory type                               Local
  Local memory size                               49152 (48KiB)
  Registers per block (NV)                        32768
  Max number of constant args                     9
  Max constant buffer size                        65536 (64KiB)
  Max size of kernel argument                     4352 (4.25KiB)
  Queue properties                                
    Out-of-order execution                        Yes
    Profiling                                     Yes
  Profiling timer resolution                      1000ns
  Execution capabilities                          
    Run OpenCL kernels                            Yes
    Run native kernels                            No
    Kernel execution timeout (NV)                 Yes
  Concurrent copy and kernel execution (NV)       Yes
    Number of async copy engines                  1
  Device Extensions                               cl_khr_global_int32_base_atomics cl_khr_global_int32_extended_atomics cl_khr_local_int32_base_atomics cl_khr_local_int32_extended_atomics cl_khr_fp64 cl_khr_byte_addressable_store cl_khr_icd cl_khr_gl_sharing cl_nv_compiler_options cl_nv_device_attribute_query cl_nv_pragma_unroll cl_nv_copy_opts cl_nv_create_buffer


NULL platform behavior
  clGetPlatformInfo(NULL, CL_PLATFORM_NAME, ...)  NVIDIA CUDA
  clGetDeviceIDs(NULL, CL_DEVICE_TYPE_ALL, ...)   Success [NV]
  clCreateContext(NULL, ...) [default]            Success [NV]
  clCreateContextFromType(NULL, CL_DEVICE_TYPE_DEFAULT)  No platform
  clCreateContextFromType(NULL, CL_DEVICE_TYPE_CPU)  No devices found in platform
  clCreateContextFromType(NULL, CL_DEVICE_TYPE_GPU)  No platform
  clCreateContextFromType(NULL, CL_DEVICE_TYPE_ACCELERATOR)  No devices found in platform
  clCreateContextFromType(NULL, CL_DEVICE_TYPE_CUSTOM)  Invalid device type for platform
  clCreateContextFromType(NULL, CL_DEVICE_TYPE_ALL)  No platform


ICD loader properties
  ICD loader Name                                 OpenCL ICD Loader
  ICD loader Vendor                               OCL Icd free software
  ICD loader Version                              2.2.11
  ICD loader Profile                              OpenCL 2.1
```
And LibreOffice now accepts OpenCL.

Nothing else than the kernel has changed between the two "clinfo" commands.

Here is some more information on my system ("inxi" command outputs):
With 5.15.0-50 kernel:
```
System:  Kernel: 5.15.0-50-generic arch: x86_64 bits: 64 compiler: gcc v: 9.4.0 Desktop: MATE v: 1.26.0
    wm: Metacity dm: LightDM Distro: Linux Mint 20.3 Una base: Ubuntu 20.04 focal
Machine:
  Type: Laptop System: ASUSTeK product: G74Sx v: 1.0 serial: <superuser required>
  Mobo: ASUSTeK model: G74Sx v: 1.0 serial: <superuser required> BIOS: American Megatrends
    v: G74Sx.203 date: 09/23/2011
Battery:
  ID-1: BAT0 charge: 40.5 Wh (100.0%) condition: 40.5/72.8 Wh (55.6%) volts: 15.5 min: 14.4
    model: ASUSTek G74--52 serial: N/A status: full
CPU:
  Info: quad core model: Intel Core i7-2670QM bits: 64 type: MT MCP arch: Sandy Bridge rev: 7
    cache: L1: 256 KiB L2: 1024 KiB L3: 6 MiB
  Speed (MHz): avg: 2908 high: 3062 min/max: 800/3100 cores: 1: 2952 2: 3055 3: 2843 4: 2868
    5: 2907 6: 3062 7: 2791 8: 2793 bogomips: 35118
  Flags: avx ht lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx
Graphics:
  Device-1: NVIDIA GF116M [GeForce GT 560M] vendor: ASUSTeK driver: nvidia v: 390.154 arch: Fermi
    pcie: speed: 5 GT/s lanes: 16 bus-ID: 01:00.0 chip-ID: 10de:1251
  Device-2: IMC Networks Integrated Webcam type: USB driver: uvcvideo bus-ID: 1-1.2:4
    chip-ID: 13d3:5134
  Display: x11 server: X.Org v: 1.20.13 with: Xwayland driver: X: loaded: nvidia
    unloaded: fbdev,modesetting,nouveau,vesa gpu: nvidia display-ID: :0 screens: 1
  Screen-1: 0 s-res: 1920x1080 s-dpi: 128
  Monitor-1: LVDS-0 res: 1920x1080 dpi: 128 diag: 438mm (17.26")
  OpenGL: renderer: GeForce GTX 560M/PCIe/SSE2 v: 4.6.0 NVIDIA 390.154 direct render: Yes
Audio:
  Device-1: Intel 6 Series/C200 Series Family High Definition Audio vendor: ASUSTeK 6
    driver: snd_hda_intel v: kernel bus-ID: 00:1b.0 chip-ID: 8086:1c20
  Device-2: NVIDIA GF116 High Definition Audio vendor: ASUSTeK driver: snd_hda_intel v: kernel
    pcie: speed: 5 GT/s lanes: 16 bus-ID: 01:00.1 chip-ID: 10de:0bee
  Sound API: ALSA v: k5.15.0-48-generic running: yes
  Sound Server-1: PulseAudio v: 13.99.1 running: yes
Network:
  Device-1: Qualcomm Atheros AR9285 Wireless Network Adapter vendor: AzureWave AW-NB037H 802.11bgn
    driver: ath9k v: kernel pcie: speed: 2.5 GT/s lanes: 1 bus-ID: 03:00.0 chip-ID: 168c:002b
  IF: wlp3s0 state: up mac: <filter>
  Device-2: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet vendor: ASUSTeK U6V/U31J
    laptop driver: r8169 v: kernel pcie: speed: 2.5 GT/s lanes: 1 port: 9000 bus-ID: 05:00.0
    chip-ID: 10ec:8168
  IF: enp5s0 state: down mac: <filter>
  IF-ID-1: vmnet1 state: unknown speed: N/A duplex: N/A mac: <filter>
  IF-ID-2: vmnet8 state: unknown speed: N/A duplex: N/A mac: <filter>
Bluetooth:
  Device-1: Qualcomm Atheros AR3011 Bluetooth type: USB driver: btusb v: 0.8 bus-ID: 1-1.1:6
    chip-ID: 0cf3:3005
  Report: hciconfig ID: hci0 rfk-id: 3 state: down bt-service: N/A rfk-block: hardware: no
    software: yes address: <filter>
Drives:
  Local Storage: total: 931.51 GiB used: 281.61 GiB (30.2%)
  ID-1: /dev/sda vendor: Crucial model: CT1000MX500SSD1 size: 931.51 GiB speed: 6.0 Gb/s
    serial: <filter>
Partition:
  ID-1: / size: 139.75 GiB used: 14.81 GiB (10.6%) fs: ext4 dev: /dev/sda1
  ID-2: /home size: 744.98 GiB used: 266.8 GiB (35.8%) fs: ext4 dev: /dev/sda2
Swap:
  ID-1: swap-1 type: partition size: 30.52 GiB used: 0 KiB (0.0%) priority: -2 dev: /dev/sda3
USB:
  Hub-1: 1-0:1 info: Full speed or root hub ports: 6 rev: 2.0 speed: 480 Mb/s chip-ID: 1d6b:0002
  Hub-2: 1-1:2 info: Intel Integrated Rate Matching Hub ports: 6 rev: 2.0 speed: 480 Mb/s
    chip-ID: 8087:0024
  Device-1: 1-1.1:6 info: Qualcomm Atheros AR3011 Bluetooth type: Bluetooth driver: btusb
    rev: 1.1 speed: 12 Mb/s chip-ID: 0cf3:3005
  Device-2: 1-1.2:4 info: IMC Networks Integrated Webcam type: Video driver: uvcvideo rev: 2.0
    speed: 480 Mb/s chip-ID: 13d3:5134
  Device-3: 1-1.4:5 info: Realtek RTS5139 Card Reader Controller type: <vendor specific>
    driver: rtsx_usb,rtsx_usb_ms,rtsx_usb_sdmmc rev: 2.0 speed: 480 Mb/s chip-ID: 0bda:0139
  Hub-3: 2-0:1 info: Full speed or root hub ports: 8 rev: 2.0 speed: 480 Mb/s chip-ID: 1d6b:0002
  Hub-4: 2-1:2 info: Intel Integrated Rate Matching Hub ports: 6 rev: 2.0 speed: 480 Mb/s
    chip-ID: 8087:0024
  Device-1: 2-1.2:3 info: Trust type: Mouse driver: hid-generic,usbhid rev: 1.1 speed: 1.5 Mb/s
    chip-ID: 145f:01d9
  Hub-5: 2-1.3:4 info: Genesys Logic Hub ports: 4 rev: 2.0 speed: 480 Mb/s chip-ID: 05e3:0608
  Device-1: 2-1.3.3:5 info: Wacom CTL-470 [Bamboo Connect] type: Mouse,HID driver: usbhid,wacom
    rev: 2.0 speed: 12 Mb/s chip-ID: 056a:00dd
  Device-2: 2-1.3.4:6 info: Microsoft Digital Media Keyboard 3000 type: Keyboard,HID
    driver: microsoft,usbhid rev: 2.0 speed: 1.5 Mb/s chip-ID: 045e:0730
  Hub-6: 3-0:1 info: Hi-speed hub with single TT ports: 1 rev: 2.0 speed: 480 Mb/s
    chip-ID: 1d6b:0002
  Hub-7: 4-0:1 info: Super-speed hub ports: 1 rev: 3.0 speed: 5 Gb/s chip-ID: 1d6b:0003
Sensors:
  System Temperatures: cpu: 70.0 C mobo: N/A gpu: nvidia temp: 61 C
  Fan Speeds (RPM): cpu: 2900
Repos:
  Packages: 2273 pm: dpkg pkgs: 2238 pm: flatpak pkgs: 35
  No active apt repos in: /etc/apt/sources.list
  Active apt repos in: /etc/apt/sources.list.d/flatpak-stable-focal.list
    1: deb http: //ppa.launchpad.net/flatpak/stable/ubuntu focal main
  Active apt repos in: /etc/apt/sources.list.d/graphics-drivers-ppa-focal.list
    1: deb http: //ppa.launchpad.net/graphics-drivers/ppa/ubuntu focal main
  Active apt repos in: /etc/apt/sources.list.d/official-package-repositories.list
    1: deb http: //packages.linuxmint.com una main upstream import backport
    2: deb http: //archive.ubuntu.com/ubuntu focal main restricted universe multiverse
    3: deb http: //archive.ubuntu.com/ubuntu focal-updates main restricted universe multiverse
    4: deb http: //archive.ubuntu.com/ubuntu focal-backports main restricted universe multiverse
    5: deb http: //security.ubuntu.com/ubuntu/ focal-security main restricted universe multiverse
    6: deb http: //archive.canonical.com/ubuntu/ focal partner
  Active apt repos in: /etc/apt/sources.list.d/tor.list
    1: deb https: //deb.torproject.org/torproject.org/ focal main
Info:
  Processes: 284 Uptime: 30m Memory: 15.6 GiB used: 1.92 GiB (12.3%) Init: systemd v: 245
  target: graphical (5) default: graphical Compilers: gcc: 9.4.0 alt: 9 Client: Unknown python3.8
  client inxi: 3.3.22
```

With 5.4.0-128 kernel:
```
System:  Kernel: 5.4.0-128-generic arch: x86_64 bits: 64 compiler: gcc v: 9.4.0 Desktop: MATE v: 1.26.0
    wm: Metacity dm: LightDM Distro: Linux Mint 20.3 Una base: Ubuntu 20.04 focal
Machine:
  Type: Laptop System: ASUSTeK product: G74Sx v: 1.0 serial: <superuser required>
  Mobo: ASUSTeK model: G74Sx v: 1.0 serial: <superuser required> BIOS: American Megatrends
    v: G74Sx.203 date: 09/23/2011
Battery:
  ID-1: BAT0 charge: 40.5 Wh (100.0%) condition: 40.5/72.8 Wh (55.6%) volts: 15.5 min: 14.4
    model: ASUSTek G74--52 serial: N/A status: full
CPU:
  Info: quad core model: Intel Core i7-2670QM bits: 64 type: MT MCP arch: Sandy Bridge rev: 7
    cache: L1: 256 KiB L2: 1024 KiB L3: 6 MiB
  Speed (MHz): avg: 2906 high: 2979 min/max: 800/3100 cores: 1: 2948 2: 2794 3: 2979 4: 2876
    5: 2814 6: 2938 7: 2964 8: 2935 bogomips: 35119
  Flags: avx ht lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx
Graphics:
  Device-1: NVIDIA GF116M [GeForce GT 560M] vendor: ASUSTeK driver: nvidia v: 390.154 arch: Fermi
    pcie: speed: 2.5 GT/s lanes: 1 bus-ID: 01:00.0 chip-ID: 10de:1251
  Device-2: IMC Networks Integrated Webcam type: USB driver: uvcvideo bus-ID: 1-1.2:4
    chip-ID: 13d3:5134
  Display: x11 server: X.Org v: 1.20.13 with: Xwayland driver: N/A note:  X driver n/a
    display-ID: :0 screens: 1
  Screen-1: 0 s-res: 1920x1080 s-dpi: 128
  Monitor-1: LVDS-0 res: 1920x1080 dpi: 128 diag: 438mm (17.26")
  OpenGL: renderer: GeForce GTX 560M/PCIe/SSE2 v: 4.6.0 NVIDIA 390.154 direct render: Yes
Audio:
  Device-1: Intel 6 Series/C200 Series Family High Definition Audio vendor: ASUSTeK 6
    driver: snd_hda_intel v: kernel bus-ID: 00:1b.0 chip-ID: 8086:1c20
  Device-2: NVIDIA GF116 High Definition Audio vendor: ASUSTeK driver: snd_hda_intel v: kernel
    pcie: speed: 5 GT/s lanes: 16 bus-ID: 01:00.1 chip-ID: 10de:0bee
  Sound API: ALSA v: k5.4.0-126-generic running: yes
  Sound Server-1: PulseAudio v: 13.99.1 running: yes
Network:
  Device-1: Qualcomm Atheros AR9285 Wireless Network Adapter vendor: AzureWave AW-NB037H 802.11bgn
    driver: ath9k v: kernel pcie: speed: 2.5 GT/s lanes: 1 bus-ID: 03:00.0 chip-ID: 168c:002b
  IF: wlp3s0 state: up mac: <filter>
  Device-2: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet vendor: ASUSTeK U6V/U31J
    laptop driver: r8169 v: kernel pcie: speed: 2.5 GT/s lanes: 1 port: 9000 bus-ID: 05:00.0
    chip-ID: 10ec:8168
  IF: enp5s0 state: down mac: <filter>
  IF-ID-1: vmnet1 state: unknown speed: N/A duplex: N/A mac: <filter>
  IF-ID-2: vmnet8 state: unknown speed: N/A duplex: N/A mac: <filter>
Bluetooth:
  Device-1: Qualcomm Atheros AR3011 Bluetooth type: USB driver: btusb v: 0.8 bus-ID: 1-1.1:3
    chip-ID: 0cf3:3005
  Report: hciconfig ID: hci0 rfk-id: 2 state: down bt-service: N/A rfk-block: hardware: no
    software: yes address: <filter>
Drives:
   Local Storage: total: 931.51 GiB used: 281.61 GiB (30.2%)
  ID-1: /dev/sda vendor: Crucial model: CT1000MX500SSD1 size: 931.51 GiB speed: 6.0 Gb/s
    serial: <filter>
Partition:
  ID-1: / size: 139.75 GiB used: 14.81 GiB (10.6%) fs: ext4 dev: /dev/sda1
  ID-2: /home size: 744.98 GiB used: 266.8 GiB (35.8%) fs: ext4 dev: /dev/sda2
Swap:
  ID-1: swap-1 type: partition size: 30.52 GiB used: 0 KiB (0.0%) priority: -2 dev: /dev/sda3
USB:
  Hub-1: 1-0:1 info: Full speed or root hub ports: 6 rev: 2.0 speed: 480 Mb/s chip-ID: 1d6b:0002
  Hub-2: 1-1:2 info: Intel Integrated Rate Matching Hub ports: 6 rev: 2.0 speed: 480 Mb/s
    chip-ID: 8087:0024
  Device-1: 1-1.1:3 info: Qualcomm Atheros AR3011 Bluetooth type: Bluetooth driver: btusb
    rev: 1.1 speed: 12 Mb/s chip-ID: 0cf3:3005
  Device-2: 1-1.2:4 info: IMC Networks Integrated Webcam type: Video driver: uvcvideo rev: 2.0
    speed: 480 Mb/s chip-ID: 13d3:5134
  Device-3: 1-1.4:5 info: Realtek RTS5139 Card Reader Controller type: <vendor specific>
    driver: rtsx_usb,rtsx_usb_ms,rtsx_usb_sdmmc rev: 2.0 speed: 480 Mb/s chip-ID: 0bda:0139
  Hub-3: 2-0:1 info: Full speed or root hub ports: 8 rev: 2.0 speed: 480 Mb/s chip-ID: 1d6b:0002
  Hub-4: 2-1:2 info: Intel Integrated Rate Matching Hub ports: 6 rev: 2.0 speed: 480 Mb/s
    chip-ID: 8087:0024
  Device-1: 2-1.2:3 info: Trust type: Mouse driver: hid-generic,usbhid rev: 1.1 speed: 1.5 Mb/s
    chip-ID: 145f:01d9
  Hub-5: 2-1.3:4 info: Genesys Logic Hub ports: 4 rev: 2.0 speed: 480 Mb/s chip-ID: 05e3:0608
  Device-1: 2-1.3.3:5 info: Wacom CTL-470 [Bamboo Connect] type: Mouse,HID driver: usbhid,wacom
    rev: 2.0 speed: 12 Mb/s chip-ID: 056a:00dd
  Device-2: 2-1.3.4:6 info: Microsoft Digital Media Keyboard 3000 type: Keyboard,HID
    driver: microsoft,usbhid rev: 2.0 speed: 1.5 Mb/s chip-ID: 045e:0730
  Hub-6: 3-0:1 info: Hi-speed hub with single TT ports: 1 rev: 2.0 speed: 480 Mb/s
    chip-ID: 1d6b:0002
  Hub-7: 4-0:1 info: Super-speed hub ports: 1 rev: 3.0 speed: 5 Gb/s chip-ID: 1d6b:0003
Sensors:
  System Temperatures: cpu: 62.0 C mobo: N/A gpu: nvidia temp: 50 C
  Fan Speeds (RPM): cpu: 2700
Repos:
  Packages: 2270 pm: dpkg pkgs: 2235 pm: flatpak pkgs: 35
  No active apt repos in: /etc/apt/sources.list
  Active apt repos in: /etc/apt/sources.list.d/flatpak-stable-focal.list
    1: deb http: //ppa.launchpad.net/flatpak/stable/ubuntu focal main
  Active apt repos in: /etc/apt/sources.list.d/graphics-drivers-ppa-focal.list
    1: deb http: //ppa.launchpad.net/graphics-drivers/ppa/ubuntu focal main
  Active apt repos in: /etc/apt/sources.list.d/official-package-repositories.list
    1: deb http: //packages.linuxmint.com una main upstream import backport
    2: deb http: //archive.ubuntu.com/ubuntu focal main restricted universe multiverse
    3: deb http: //archive.ubuntu.com/ubuntu focal-updates main restricted universe multiverse
    4: deb http: //archive.ubuntu.com/ubuntu focal-backports main restricted universe multiverse
    5: deb http: //security.ubuntu.com/ubuntu/ focal-security main restricted universe multiverse
    6: deb http: //archive.canonical.com/ubuntu/ focal partner
  Active apt repos in: /etc/apt/sources.list.d/tor.list
    1: deb https: //deb.torproject.org/torproject.org/ focal main
Info:
  Processes: 254 Uptime: 54m Memory: 15.61 GiB used: 1.15 GiB (7.4%) Init: systemd v: 245
  target: graphical (5) default: graphical Compilers: gcc: 9.4.0 alt: 9 Client: Unknown python3.8
  client inxi: 3.3.22
```

In both cases, installed graphics driver is "nvidia-driver-390", 390.154-0ubuntu0.20.04.1.

I have tried to report this bug through Launchpad, but I always get the same connexion error:
```
**Oops!**

[COLOR=#333333][FONT=Ubuntu]Sorry, something just went wrong in Launchpad.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]We’ve recorded what happened, and we’ll fix it as soon as possible. Apologies for the inconvenience.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]**If you can't login**, join us on [#launchpad IRC channel]("irc://irc.libera.chat/launchpad") at irc.libera.chat, [EMAIL="feedback@launchpad.net"]e-mail us[/EMAIL] or visit our [feedback page]("https://help.launchpad.net/Feedback").[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]If you [report this as a bug]("https://launchpad.net/launchpad/+filebug"), please include the error ID below, preferably by copying and pasting it rather than by taking a screenshot.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu](Error ID: OOPS-53c450d8416da5efe13b1411e11d7719)[/FONT][/COLOR]

```

Regards,

MN

---

### Post by coffeecat on 2022-10-16
*Thread moved to **Mint** sub-forum.*

@mikenavy, I have replaced the BBCode quote tags with code tags in your post. See how this restores/preserves vertical formatting which was lost with the quote tags. There is a link in my sig about using code tags if you need it.

---

### Post by mikenavy on 2022-10-17
> **coffeecat said:**
> *Thread moved to **Mint** sub-forum.*

@mikenavy, I have replaced the BBCode quote tags with code tags in your post. See how this restores/preserves vertical formatting which was lost with the quote tags. There is a link in my sig about using code tags if you need it.
Hi,

OK for code tags.

I don't agree with thread moved to Mint sub-forum. This problem is related to kernel 5.15.0-50, written and supplied by Ubuntu, and its failure in recognizing GTX 560 M as an OpenCL platform, with Nvidia driver [COLOR=#000000]390.154-0ubuntu0.20.04.1[/COLOR] supplied by Ubuntu. 

So, in the absence of a kernel dedicated sub-forum, I think the hardware one is the good one.

(NB: Linux Mint just supplies some Xapps, the Mate 1.26 desktop and makes the distribution; in this problem, nothing from Linux Mint is concerned).

Regards,

MN

---

