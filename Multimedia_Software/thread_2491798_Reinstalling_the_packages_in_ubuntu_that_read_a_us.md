---
title: "Reinstalling the packages in ubuntu that read a usb dvd writter"
date: 2023-10-20
forum: Multimedia Software
---

### Post by send2 on 2023-10-20
Hello all,

Not sure if I need to post this here or in hardware section. I am using Ubuntu 22.04.3 and I was using a cd with pdf's with no problem when I moved the computer to show something to someone and the usb disconnected, I could not get the usb dvd writer to connect properly again, it keeps connecting and disconnecting the dvd writer and it can't load the contents of disc. As a matter of fact, it caused Ubuntu to freeze, and it took several tries to get Ubuntu back. The dvd writer is an LG ultra slim portable model gp65. It is working well in Windows but it seems to have corrupted the drivers that read DVDs in Ubuntu. How do I reinstall those particular packages to restore functionality of dvd writer again? I am using Ubuntu 22.04.3 in VMware with Windows 11 as host. 

```
~$ lsusb
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 0e0f:0002 VMware, Inc. Virtual USB Hub
Bus 003 Device 003: ID 0e0f:0002 VMware, Inc. Virtual USB Hub
Bus 003 Device 020: ID 0e8d:1887 MediaTek Inc. Slim Portable DVD Writer
Bus 003 Device 002: ID 0e0f:0003 VMware, Inc. Virtual Mouse
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0e0f:0002 VMware, Inc. Virtual USB Hub
Bus 001 Device 002: ID 0e0f:0008 VMware, Inc. Virtual Bluetooth Adapter
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
```

My inxi -Fazi:

```
System:
  Kernel: 6.2.0-35-generic x86_64 bits: 64 compiler: N/A
    parameters: BOOT_IMAGE=/boot/vmlinuz-6.2.0-35-generic
    root=UUID=cf642b79-3713-4822-9aaf-3f7ecb8eca08 ro
    find_preseed=/preseed.cfg auto noprompt priority=critical locale=en_US
    quiet splash
  Desktop: GNOME 42.9 tk: GTK 3.24.33 wm: gnome-shell dm: GDM3 42.0
    Distro: Ubuntu 22.04.3 LTS (Jammy Jellyfish)
Machine:
  Type: Vmware System: VMware product: VMware Virtual Platform v: N/A
    serial: <superuser required> Chassis: No Enclosure type: 1
    serial: <superuser required>
  Mobo: Intel model: 440BX Desktop Reference Platform
    serial: <superuser required> BIOS: Phoenix v: 6.00 date: 11/12/2020
CPU:
  Info: model: AMD Ryzen 7 5700U with Radeon Graphics bits: 64 type: SMP
    arch: Zen 2 family: 0x17 (23) model-id: 0x68 (104) stepping: 1
    microcode: N/A
  Topology: cpus: 2x cores: 1 smt: <unsupported> cache:
    L1: 2x 64 KiB (128 KiB) desc: d-1x32 KiB; i-1x32 KiB
    L2: 2x 512 KiB (1024 KiB) desc: 1x512 KiB L3: 2x 4 MiB (8 MiB)
    desc: 1x4 MiB
  Speed (MHz): avg: 1797 min/max: N/A cores: 1: 1797 2: 1797 bogomips: 7186
  Flags: avx avx2 lm nx pae sse sse2 sse3 sse4_1 sse4_2 sse4a ssse3
  Vulnerabilities:
  Type: gather_data_sampling status: Not affected
  Type: itlb_multihit status: Not affected
  Type: l1tf status: Not affected
  Type: mds status: Not affected
  Type: meltdown status: Not affected
  Type: mmio_stale_data status: Not affected
  Type: retbleed mitigation: untrained return thunk; SMT disabled
  Type: spec_rstack_overflow mitigation: SMT disabled
  Type: spec_store_bypass
    mitigation: Speculative Store Bypass disabled via prctl
  Type: spectre_v1
    mitigation: usercopy/swapgs barriers and __user pointer sanitization
  Type: spectre_v2 mitigation: Retpolines, IBPB: conditional, STIBP:
    disabled, RSB filling, PBRSB-eIBRS: Not affected
  Type: srbds status: Not affected
  Type: tsx_async_abort status: Not affected
Graphics:
  Device-1: VMware SVGA II Adapter driver: vmwgfx v: 2.20.0.0 ports:
    active: Virtual-1 empty: Virtual-2, Virtual-3, Virtual-4, Virtual-5,
    Virtual-6, Virtual-7, Virtual-8
    bus-ID: 00:0f.0 chip-ID: 15ad:0405 class-ID: 0300
  Display: wayland server: X.Org v: 1.22.1.1 with: Xwayland v: 22.1.1
    compositor: gnome-shell driver: gpu: vmwgfx display-ID: :0 screens: 1
  Screen-1: 0 s-res: 1920x1080 s-dpi: 96 s-size: 508x285mm (20.0x11.2")
    s-diag: 582mm (22.9")
  Monitor-1: XWAYLAND0 mapped: Virtual-1 res: 1920x1080 hz: 60 size: N/A
    modes: max: 1920x1080 min: 640x480
  OpenGL: renderer: SVGA3D; build: RELEASE; LLVM;
    v: 4.3 Mesa 23.0.4-0ubuntu1~22.04.1 direct render: Yes
Audio:
  Device-1: Ensoniq ES1371/ES1373 / Creative Labs CT2518 driver: snd_ens1371
    v: kernel bus-ID: 02:02.0 chip-ID: 1274:1371 class-ID: 0401
  Sound Server-1: ALSA v: k6.2.0-35-generic running: yes
  Sound Server-2: PulseAudio v: 15.99.1 running: yes
  Sound Server-3: PipeWire v: 0.3.48 running: yes
Network:
  Device-1: Intel 82371AB/EB/MB PIIX4 ACPI vendor: VMware Virtual Machine
    type: network bridge driver: N/A modules: i2c_piix4 port: N/A
    bus-ID: 00:07.3 chip-ID: 8086:7113 class-ID: 0680
  Device-2: Intel 82545EM Gigabit Ethernet
    vendor: VMware PRO/1000 MT Single Port driver: e1000 v: kernel port: 2000
    bus-ID: 02:01.0 chip-ID: 8086:100f class-ID: 0200
  IF: ens33 state: up speed: 1000 Mbps duplex: full mac: <filter>
  IP v4: <filter> type: dynamic noprefixroute scope: global
    broadcast: <filter>
  IP v6: <filter> type: noprefixroute scope: link
  WAN IP: <filter>
Bluetooth:
  Device-1: VMware Virtual Bluetooth Adapter type: USB driver: btusb v: 0.8
    bus-ID: 1-1:2 chip-ID: 0e0f:0008 class-ID: e001 serial: <filter>
  Report: hciconfig ID: hci0 rfk-id: 0 state: down
    bt-service: enabled,running rfk-block: hardware: no software: no
    address: <filter>
  Info: acl-mtu: 8192:128 sco-mtu: 64:128
    link-policy: rswitch hold sniff park link-mode: peripheral accept
Drives:
  Local Storage: total: 120 GiB used: 322.45 GiB (268.7%)
  SMART Message: Required tool smartctl not installed. Check --recommends
  ID-1: /dev/sda maj-min: 8:0 vendor: VMware model: Virtual S size: 120 GiB
    block-size: physical: 512 B logical: 512 B type: N/A serial: N/A rev: 1.0
    scheme: GPT
Partition:
  ID-1: / raw-size: 119.5 GiB size: 117.06 GiB (97.96%)
    used: 21.89 GiB (18.7%) fs: ext4 dev: /dev/sda3 maj-min: 8:3
  ID-2: /boot/efi raw-size: 513 MiB size: 512 MiB (99.80%)
    used: 6.1 MiB (1.2%) fs: vfat dev: /dev/sda2 maj-min: 8:2
Swap:
  Kernel: swappiness: 60 (default) cache-pressure: 100 (default)
  ID-1: swap-1 type: file size: 3.81 GiB used: 524 KiB (0.0%) priority: -2
    file: /swapfile
Sensors:
  Message: No sensor data found. Is lm-sensors configured?
Info:
  Processes: 305 Uptime: 37m wakeups: 2781 Memory: 3.78 GiB
  used: 2.15 GiB (56.9%) Init: systemd v: 249 runlevel: 5 tool: systemctl
  Compilers: gcc: 11.4.0 alt: 11/12 Packages: 2235 apt: 2217 lib: 1211
  snap: 18 Shell: Bash v: 5.1.16 running-in: gnome-terminal inxi: 3.3.13

```

Any other bits of information that I can provide, just let me know. Thanks in advance.

Edit: Go figure, the minute I write asking for help and this time the problem got solved. After leaving the dvd writer disconnected for several reboots, it started working again. I automatically started playing the cd with no problem. I love Ubuntu.

---

