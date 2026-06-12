---
title: "Problem with Sound."
date: 2018-07-18
forum: Multimedia Software
---

### Post by sangamswadik on 2018-07-18
Hello.
I noticed after yesterday's update,headphones are not getting detected,But I'm able to hear from the speaker.
I'm using it through pavucontrol but the sound is not clear there is some kind of noise.

```
00:00.0 Host bridge: Intel Corporation Device 3ec2 (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Device 3e92
00:12.0 Signal processing controller: Intel Corporation Device a379 (rev 10)
00:14.0 USB controller: Intel Corporation Device a36d (rev 10)
00:14.2 RAM memory: Intel Corporation Device a36f (rev 10)
00:16.0 Communication controller: Intel Corporation Device a360 (rev 10)
00:17.0 SATA controller: Intel Corporation Device a352 (rev 10)
00:1c.0 PCI bridge: Intel Corporation Device a33f (rev f0)
00:1f.0 ISA bridge: Intel Corporation Device a303 (rev 10)
00:1f.3 Audio device: Intel Corporation Device a348 (rev 10)
00:1f.4 SMBus: Intel Corporation Device a323 (rev 10)
00:1f.5 Serial bus controller [0c80]: Intel Corporation Device a324 (rev 10)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 16)

```

And this 

```
lspci -v
00:00.0 Host bridge: Intel Corporation Device 3ec2 (rev 07)
    Subsystem: Gigabyte Technology Co., Ltd Device 5000
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation Device 3e92 (prog-if 00 [VGA controller])
    Subsystem: Gigabyte Technology Co., Ltd Device d000
    Flags: bus master, fast devsel, latency 0, IRQ 126
    Memory at a0000000 (64-bit, non-prefetchable) [size=16M]
    Memory at 90000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 4000 [size=64]
    [virtual] Expansion ROM at 000c0000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

00:12.0 Signal processing controller: Intel Corporation Device a379 (rev 10)
    Subsystem: Gigabyte Technology Co., Ltd Device 8888
    Flags: fast devsel, IRQ 16
    Memory at a121c000 (64-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: intel_pch_thermal
    Kernel modules: intel_pch_thermal

00:14.0 USB controller: Intel Corporation Device a36d (rev 10) (prog-if 30 [XHCI])
    Subsystem: Gigabyte Technology Co., Ltd Device 5007
    Flags: bus master, medium devsel, latency 0, IRQ 123
    Memory at a1200000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: xhci_hcd

00:14.2 RAM memory: Intel Corporation Device a36f (rev 10)
    Subsystem: Intel Corporation Device 7270
    Flags: fast devsel
    Memory at a1216000 (64-bit, non-prefetchable) [disabled] [size=8K]
    Memory at a121b000 (64-bit, non-prefetchable) [disabled] [size=4K]
    Capabilities: <access denied>

00:16.0 Communication controller: Intel Corporation Device a360 (rev 10)
    Subsystem: Gigabyte Technology Co., Ltd Device 1c3a
    Flags: bus master, fast devsel, latency 0, IRQ 127
    Memory at a121a000 (64-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: mei_me
    Kernel modules: mei_me

00:17.0 SATA controller: Intel Corporation Device a352 (rev 10) (prog-if 01 [AHCI 1.0])
    Subsystem: Gigabyte Technology Co., Ltd Device b005
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 124
    Memory at a1214000 (32-bit, non-prefetchable) [size=8K]
    Memory at a1219000 (32-bit, non-prefetchable) [size=256]
    I/O ports at 4070 [size=8]
    I/O ports at 4060 [size=4]
    I/O ports at 4040 [size=32]
    Memory at a1218000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ahci
    Kernel modules: ahci

00:1c.0 PCI bridge: Intel Corporation Device a33f (rev f0) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 122
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: a1100000-a11fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1f.0 ISA bridge: Intel Corporation Device a303 (rev 10)
    Subsystem: Gigabyte Technology Co., Ltd Device 5001
    Flags: bus master, medium devsel, latency 0

00:1f.3 Audio device: Intel Corporation Device a348 (rev 10)
    Subsystem: Gigabyte Technology Co., Ltd Device a182
    Flags: bus master, fast devsel, latency 32, IRQ 128
    Memory at a1210000 (64-bit, non-prefetchable) [size=16K]
    Memory at a1000000 (64-bit, non-prefetchable) [size=1M]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel

00:1f.4 SMBus: Intel Corporation Device a323 (rev 10)
    Subsystem: Gigabyte Technology Co., Ltd Device 5001
    Flags: medium devsel
    Memory at 8f800000 (64-bit, non-prefetchable) [disabled] [size=256]
    I/O ports at efa0 [size=32]
    Kernel modules: i2c_i801

00:1f.5 Serial bus controller [0c80]: Intel Corporation Device a324 (rev 10)
    Subsystem: Intel Corporation Device 7270
    Flags: fast devsel
    Memory at fe010000 (32-bit, non-prefetchable) [size=4K]

01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 16)
    Subsystem: Gigabyte Technology Co., Ltd Onboard Ethernet
    Flags: bus master, fast devsel, latency 0, IRQ 125
    I/O ports at 3000 [size=256]
    Memory at a1104000 (64-bit, non-prefetchable) [size=4K]
    Memory at a1100000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: r8169
    Kernel modules: r8169

```

Can anyone please help me ?
Thanks.

---

### Post by sangamswadik on 2018-07-18
I tried the the solution posted at FOSS but it does not help me.
[https://itsfoss.com/fix-sound-ubuntu-1304-quick-tip/](https://itsfoss.com/fix-sound-ubuntu-1304-quick-tip/)

---

### Post by sangamswadik on 2018-07-18
Here pulseaudio --vv
>  pulseaudio -vv
I: [pulseaudio] main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
I: [pulseaudio] main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
D: [pulseaudio] core-rtclock.c: Timer slack is set to 50 us.
D: [pulseaudio] core-util.c: RealtimeKit worked.
I: [pulseaudio] core-util.c: Successfully gained nice level -11.
I: [pulseaudio] main.c: This is PulseAudio 11.1
D: [pulseaudio] main.c: Compilation host: x86_64-pc-linux-gnu
D: [pulseaudio] main.c: Compilation CFLAGS: -g -O2 -fdebug-prefix-map=/build/pulseaudio-EOwPuF/pulseaudio-11.1=. -fstack-protector-strong -Wformat -Werror=format-security -Wall -W -Wextra -pipe -Wno-long-long -Wno-overlength-strings -Wunsafe-loop-optimizations -Wundef -Wformat=2 -Wlogical-op -Wsign-compare -Wformat-security -Wmissing-include-dirs -Wformat-nonliteral -Wpointer-arith -Winit-self -Wdeclaration-after-statement -Wfloat-equal -Wmissing-prototypes -Wredundant-decls -Wmissing-declarations -Wmissing-noreturn -Wshadow -Wendif-labels -Wcast-align -Wstrict-aliasing -Wwrite-strings -Wno-unused-parameter -ffast-math -fno-common -fdiagnostics-show-option -fdiagnostics-color=auto
D: [pulseaudio] main.c: Running on host: Linux x86_64 4.15.0-23-generic #25-Ubuntu SMP Wed May 23 18:02:16 UTC 2018
D: [pulseaudio] main.c: Found 6 CPUs.
I: [pulseaudio] main.c: Page size is 4096 bytes
D: [pulseaudio] main.c: Compiled with Valgrind support: no
D: [pulseaudio] main.c: Running in valgrind mode: no
D: [pulseaudio] main.c: Running in VM: no
D: [pulseaudio] main.c: Optimized build: yes
D: [pulseaudio] main.c: FASTPATH defined, only fast path asserts disabled.
I: [pulseaudio] main.c: Machine ID is 9a0f8fdb2c0e41baa3d2c254251518e8.
I: [pulseaudio] main.c: Session ID is 2.
I: [pulseaudio] main.c: Using runtime directory /run/user/1000/pulse.
I: [pulseaudio] main.c: Using state directory /home/ubuntu/.config/pulse.
I: [pulseaudio] main.c: Using modules directory /usr/lib/pulse-11.1/modules.
I: [pulseaudio] main.c: Running in system mode: no
E: [pulseaudio] pid.c: Daemon already running.
E: [pulseaudio] main.c: pa_pid_file_create() failed.



---

### Post by nik.charles on 2018-08-26
Assuming update included new version of Pulseaudio try removing home folder configuration

```
rm -r ~/.config/pulse/*
```

reboot pc for Pulseaudio to rebuild new set of configuration files

---

