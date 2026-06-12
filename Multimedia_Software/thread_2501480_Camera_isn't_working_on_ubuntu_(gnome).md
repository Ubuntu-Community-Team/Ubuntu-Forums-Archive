---
title: "Camera isn't working on ubuntu (gnome)"
date: 2024-10-09
forum: Multimedia Software
---

### Post by yunhxc on 2024-10-09
When I try to use it appears this message: No Camera Found, Connect a camera device.
Any solution? Thanks a lot.

---

### Post by ajgreeny on 2024-10-09
With no information about your hardware it is difficult to answer you or give you an immediate solution.

For a first move please show us the outputs of the three terminal commands
```
inxi -Fzx
lsusb
lspci
```
Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

---

### Post by yancek on 2024-10-09
In addition to giving information requested above, it might help if you explain what 'I try to use it' means.  How do you try to access it?  What software are you using?

---

### Post by yunhxc on 2024-10-09
Sorry, My laptop is an HP 240-G5

---

### Post by yunhxc on 2024-10-09
```
~$ inxi -Fzx
System:
  Kernel: 6.8.0-45-generic arch: x86_64 bits: 64 compiler: gcc v: 13.2.0
  Desktop: GNOME v: 46.0 Distro: Ubuntu 24.04.1 LTS (Noble Numbat)
Machine:
  Type: Laptop System: HP product: HP 240 G5 Notebook PC v: CNB1
    serial: <superuser required>
  Mobo: HP model: 81DF v: KBC Version 70.12 serial: <superuser required>
    UEFI: Insyde v: F.09 date: 05/09/2016
Battery:
  ID-1: BAT0 charge: 10.7 Wh (31.6%) condition: 33.9/33.9 Wh (100.0%)
    volts: 14.3 min: 14.8 model: Hewlett-Packard Primary status: discharging
CPU:
  Info: dual core model: Intel Core i3-5005U bits: 64 type: MT MCP
    arch: Broadwell rev: 4 cache: L1: 128 KiB L2: 512 KiB L3: 3 MiB
  Speed (MHz): avg: 800 high: 1401 min/max: 500/1900 cores: 1: 500 2: 1401
    3: 800 4: 500 bogomips: 16000
  Flags: avx avx2 ht lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx
Graphics:
  Device-1: Intel HD Graphics 5500 vendor: Hewlett-Packard driver: i915
    v: kernel arch: Gen-8 bus-ID: 00:02.0
  Device-2: Cheng Uei Precision Industry (Foxlink) HP TrueVision HD
    driver: uvcvideo type: USB bus-ID: 1-1.5:3
  Display: wayland server: X.Org v: 23.2.6 with: Xwayland v: 23.2.6
    compositor: gnome-shell driver: dri: iris gpu: i915
    resolution: 1366x768~60Hz
  API: EGL v: 1.5 drivers: iris,swrast platforms:
    active: wayland,x11,surfaceless,device inactive: gbm
  API: OpenGL v: 4.6 compat-v: 4.5 vendor: intel mesa v: 24.0.9-0ubuntu0.1
    glx-v: 1.4 direct-render: yes renderer: Mesa Intel HD Graphics 5500 (BDW
    GT2)
Audio:
  Device-1: Intel Broadwell-U Audio vendor: Hewlett-Packard
    driver: snd_hda_intel v: kernel bus-ID: 00:03.0
  Device-2: Intel Wildcat Point-LP High Definition Audio
    vendor: Hewlett-Packard driver: snd_hda_intel v: kernel bus-ID: 00:1b.0
  API: ALSA v: k6.8.0-45-generic status: kernel-api
  Server-1: PipeWire v: 1.0.5 status: active
Network:
  Device-1: Realtek RTL8111/8168/8211/8411 PCI Express Gigabit Ethernet
    vendor: Hewlett-Packard RTL8111/8168/8411 driver: r8169 v: kernel port: 3000
    bus-ID: 01:00.0
  IF: enp1s0 state: down mac: <filter>
  Device-2: Broadcom BCM43142 802.11b/g/n vendor: Hewlett-Packard driver: wl
    v: kernel bus-ID: 02:00.0
  IF: wlp2s0 state: up mac: <filter>
Bluetooth:
  Device-1: Broadcom BCM43142A0 Bluetooth 4.0 driver: btusb v: 0.8 type: USB
    bus-ID: 1-1.6:4
  Report: hciconfig ID: hci0 rfk-id: 2 state: down
    bt-service: enabled,running rfk-block: hardware: no software: no
    address: <filter>
Drives:
  Local Storage: total: 465.76 GiB used: 14.62 GiB (3.1%)
  ID-1: /dev/sda vendor: HGST (Hitachi) model: HTS725050A7E630
    size: 465.76 GiB
Partition:
  ID-1: / size: 456.35 GiB used: 14.61 GiB (3.2%) fs: ext4 dev: /dev/sda2
  ID-2: /boot/efi size: 1.05 GiB used: 6.1 MiB (0.6%) fs: vfat
    dev: /dev/sda1
Swap:
  ID-1: swap-1 type: file size: 3.74 GiB used: 0 KiB (0.0%) file: /swap.img
Sensors:
  System Temperatures: cpu: 31.0 C mobo: N/A
  Fan Speeds (rpm): N/A
Info:
  Memory: total: 4 GiB available: 3.74 GiB used: 1.86 GiB (49.7%)
  Processes: 228 Uptime: 6m Init: systemd target: graphical (5)
  Packages: 1768 Compilers: gcc: 13.2.0 Shell: Bash v: 5.2.21 inxi: 3.3.34
```
```
~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8001 Intel Corp. Integrated Hub
Bus 001 Device 003: ID 05c8:038f Cheng Uei Precision Industry Co., Ltd (Foxlink) HP TrueVision HD
Bus 001 Device 004: ID 0a5c:216d Broadcom Corp. BCM43142A0 Bluetooth 4.0
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
```

```
~$ lspci
00:00.0 Host bridge: Intel Corporation Broadwell-U Host Bridge -OPI (rev 09)
00:02.0 VGA compatible controller: Intel Corporation HD Graphics 5500 (rev 09)
00:03.0 Audio device: Intel Corporation Broadwell-U Audio Controller (rev 09)
00:04.0 Signal processing controller: Intel Corporation Broadwell-U Processor Thermal Subsystem (rev 09)
00:14.0 USB controller: Intel Corporation Wildcat Point-LP USB xHCI Controller (rev 03)
00:16.0 Communication controller: Intel Corporation Wildcat Point-LP MEI Controller #1 (rev 03)
00:1b.0 Audio device: Intel Corporation Wildcat Point-LP High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #1 (rev e3)
00:1c.1 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #2 (rev e3)
00:1d.0 USB controller: Intel Corporation Wildcat Point-LP USB EHCI Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation Wildcat Point-LP LPC Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation Wildcat Point-LP SATA Controller [AHCI Mode] (rev 03)
00:1f.3 SMBus: Intel Corporation Wildcat Point-LP SMBus Controller (rev 03)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8211/8411 PCI Express Gigabit Ethernet Controller (rev 15)
02:00.0 Network controller: Broadcom Inc. and subsidiaries BCM43142 802.11b/g/n (rev 01)
```

---

### Post by ajgreeny on 2024-10-09
And as **yancec** said,  it might help if you explain what 'I try to use it' means. How do you try to access it? What software are you using?

I have never found **cheese**, which used to be the default application in Ubuntu, to be very good and have always used **guvcviw** instead.

---

