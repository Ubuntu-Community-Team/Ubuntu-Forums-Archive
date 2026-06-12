---
title: "Cant see front panel audio jacks"
date: 2022-10-29
forum: MINT
---

### Post by ztrix on 2022-10-29
In WIndows there was an option in Realtek HD Audio Manager to turn these jacks on. But now, when i moved to Linux, I cant see them in audio device manager, and I dont know what to do
I tried these things with alsa-mixer, but to no result. I am very new to Linux
There is my sysinfo
```

System:
  Kernel: 5.15.0-41-generic x86_64 bits: 64 compiler: gcc v: 11.2.0 Desktop: Cinnamon 5.4.12
    tk: GTK 3.24.33 wm: Mutter dm: LightDM Distro: Linux Mint 21 Vanessa base: Ubuntu 22.04 jammy
Machine:
  Type: Desktop Mobo: ASRock model: H310CM-HDV serial: <superuser required>
    UEFI: American Megatrends v: P4.20 date: 05/14/2019
CPU:
  Info: quad core model: Intel Core i3-9100F bits: 64 type: MCP arch: Coffee Lake rev: B cache:
    L1: 256 KiB L2: 1024 KiB L3: 6 MiB
  Speed (MHz): avg: 4079 high: 4092 min/max: 800/4200 cores: 1: 4064 2: 4092 3: 4072 4: 4090
    bogomips: 28800
  Flags: avx avx2 ht lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx
Graphics:
  Device-1: NVIDIA GM107 [GeForce GTX 750] driver: nouveau v: kernel pcie: speed: 2.5 GT/s
    lanes: 16 ports: active: DVI-I-1 empty: DVI-D-1,HDMI-A-1 bus-ID: 01:00.0 chip-ID: 10de:1381
  Device-2: Aveo UVC camera (Bresser microscope) type: USB driver: uvcvideo bus-ID: 1-9:4
    chip-ID: 1871:0101
  Display: x11 server: X.Org v: 1.21.1.3 driver: X: loaded: modesetting unloaded: fbdev,vesa
    gpu: nouveau display-ID: :0 screens: 1
  Screen-1: 0 s-res: 1920x1080 s-dpi: 96
  Monitor-1: DVI-I-1 model: Philips PHL 224E5 res: 1920x1080 dpi: 102 diag: 546mm (21.5")
  OpenGL: renderer: NV117 v: 4.3 Mesa 22.0.5 direct render: Yes
Audio:
  Device-1: Intel 200 Series PCH HD Audio vendor: ASRock driver: snd_hda_intel v: kernel
    bus-ID: 00:1f.3 chip-ID: 8086:a2f0
  Device-2: NVIDIA GM107 High Definition Audio [GeForce 940MX] driver: snd_hda_intel v: kernel
    pcie: speed: 2.5 GT/s lanes: 16 bus-ID: 01:00.1 chip-ID: 10de:0fbc
  Sound Server-1: ALSA v: k5.15.0-41-generic running: yes
  Sound Server-2: PulseAudio v: 15.99.1 running: yes
  Sound Server-3: PipeWire v: 0.3.48 running: yes
Network:
  Device-1: Realtek RTL8192EE PCIe Wireless Network Adapter driver: rtl8192ee v: kernel pcie:
    speed: 2.5 GT/s lanes: 1 port: d000 bus-ID: 02:00.0 chip-ID: 10ec:818b
  IF: wlp2s0 state: down mac: <filter>
  Device-2: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet vendor: ASRock driver: r8169
    v: kernel pcie: speed: 2.5 GT/s lanes: 1 port: c000 bus-ID: 03:00.0 chip-ID: 10ec:8168
  IF: enp3s0 state: up speed: 100 Mbps duplex: full mac: <filter>
Drives:
  Local Storage: total: 937.11 GiB used: 12.14 GiB (1.3%)
  ID-1: /dev/sda vendor: Western Digital model: WD7501AALS-00E3A0 size: 698.64 GiB
    speed: 3.0 Gb/s serial: <filter>
  ID-2: /dev/sdb vendor: HP model: SSD S700 Pro 256GB size: 238.47 GiB speed: 6.0 Gb/s
    serial: <filter>
Partition:
  ID-1: / size: 233.18 GiB used: 12.14 GiB (5.2%) fs: ext4 dev: /dev/sdb2
  ID-2: /boot/efi size: 511 MiB used: 5.2 MiB (1.0%) fs: vfat dev: /dev/sdb1
Swap:
  ID-1: swap-1 type: file size: 2 GiB used: 0 KiB (0.0%) priority: -2 file: /swapfile
USB:
  Hub-1: 1-0:1 info: Hi-speed hub with single TT ports: 10 rev: 2.0 speed: 480 Mb/s
    chip-ID: 1d6b:0002
  Device-1: 1-1:2 info: USB OPTICAL MOUSE type: Mouse driver: hid-generic,usbhid rev: 1.1
    speed: 1.5 Mb/s chip-ID: 0000:3825
  Device-2: 1-2:3 info: China Resource Semico USB Keyboard type: Keyboard,HID
    driver: hid-generic,usbhid rev: 1.1 speed: 1.5 Mb/s chip-ID: 1a2c:4b44
  Device-3: 1-9:4 info: Aveo UVC camera (Bresser microscope) type: Video driver: uvcvideo
    rev: 2.0 speed: 480 Mb/s chip-ID: 1871:0101
  Hub-2: 2-0:1 info: Super-speed hub ports: 4 rev: 3.0 speed: 5 Gb/s chip-ID: 1d6b:0003
Sensors:
  System Temperatures: cpu: 48.0 C mobo: N/A gpu: nouveau temp: 38.0 C
  Fan Speeds (RPM): N/A gpu: nouveau fan: 3720
Repos:
  Packages: apt: 2210
  No active apt repos in: /etc/apt/sources.list
  Active apt repos in: /etc/apt/sources.list.d/official-package-repositories.list
    1: deb http: //packages.linuxmint.com vanessa main upstream import backport
    2: deb http: //archive.ubuntu.com/ubuntu jammy main restricted universe multiverse
    3: deb http: //archive.ubuntu.com/ubuntu jammy-updates main restricted universe multiverse
    4: deb http: //archive.ubuntu.com/ubuntu jammy-backports main restricted universe multiverse
    5: deb http: //security.ubuntu.com/ubuntu/ jammy-security main restricted universe multiverse
Info:
  Processes: 263 Uptime: 37m Memory: 11.63 GiB used: 3.03 GiB (26.1%) Init: systemd v: 249
  runlevel: 5 Compilers: gcc: 11.3.0 alt: 11 Client: Unknown python3.10 client inxi: 3.3.13


```

---

### Post by jeremy31 on 2022-10-29
Moved to Mint subforum

---

### Post by ztrix on 2022-10-30
Everything solved by switching Front Panel setting in BIOS from HD to AC 97

---

