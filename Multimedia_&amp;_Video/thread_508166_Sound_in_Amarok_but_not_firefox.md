---
title: "Sound in Amarok but not firefox"
date: 2007-07-23
forum: Multimedia &amp; Video
---

### Post by iamstretchypanda on 2007-07-23
I have onboard sound on my A8N32-SLI (realtek ALC850).  Everything worked great, sound worked from startup, sound in mythtv, sound in firefox, but once i finished configuring and installed games i relized there was no sound in Americas Army or Counterstrike.  I followed various guides tweaking some settings changing things from OSS to ALSA.  Sound started working in games, still works in Amarok, and still works in movie player.

results for aplay -l

```
**** List of PLAYBACK Hardware Devices ****
ALSA lib conf.c:1587:(snd_config_load1) _toplevel_:34:0:Unexpected char
ALSA lib conf.c:2848:(snd_config_hook_load) /home/iamstretchypanda/.asoundrc may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2712:(snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3075:(snd_config_update_r) hooks failed, removing configuration
aplay: device_list:231: control open (0): Invalid argument
ALSA lib conf.c:1587:(snd_config_load1) _toplevel_:34:0:Unexpected char
ALSA lib conf.c:2848:(snd_config_hook_load) /home/iamstretchypanda/.asoundrc may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2712:(snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3075:(snd_config_update_r) hooks failed, removing configuration
aplay: device_list:231: control open (1): Invalid argument
ALSA lib conf.c:1587:(snd_config_load1) _toplevel_:34:0:Unexpected char
ALSA lib conf.c:2848:(snd_config_hook_load) /home/iamstretchypanda/.asoundrc may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2712:(snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3075:(snd_config_update_r) hooks failed, removing configuration
aplay: device_list:231: control open (2): Invalid argument
```

Results for alsamixer:

```
ALSA lib conf.c:1587:(snd_config_load1) _toplevel_:34:0:Unexpected char
ALSA lib conf.c:2848:(snd_config_hook_load) /home/iamstretchypanda/.asoundrc may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2712:(snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3075:(snd_config_update_r) hooks failed, removing configuration

alsamixer: function snd_ctl_open failed for default: Invalid argument
```

results for lspci -v

```
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
        Subsystem: ASUSTeK Computer Inc. Unknown device 81d2
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: <access denied>

00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
        Subsystem: ASUSTeK Computer Inc. Unknown device 81d2
        Flags: 66MHz, fast devsel

00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
        Subsystem: ASUSTeK Computer Inc. Unknown device 81d2
        Flags: 66MHz, fast devsel

00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
        Subsystem: ASUSTeK Computer Inc. Unknown device 81d2
        Flags: 66MHz, fast devsel

00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
        Subsystem: ASUSTeK Computer Inc. Unknown device 81d2
        Flags: bus master, 66MHz, fast devsel, latency 0

00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
        Subsystem: ASUSTeK Computer Inc. Unknown device 81d2
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: <access denied>

00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
        Subsystem: ASUSTeK Computer Inc. Unknown device 81d2
        Flags: 66MHz, fast devsel

00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
        Subsystem: ASUSTeK Computer Inc. Unknown device 81d2
        Flags: 66MHz, fast devsel

00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 0000a000-0000afff
        Memory behind bridge: fa600000-fa7fffff
        Capabilities: <access denied>

00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 0000b000-0000bfff
        Memory behind bridge: fa800000-fa8fffff
        Capabilities: <access denied>

00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        I/O behind bridge: 0000c000-0000cfff
        Memory behind bridge: fa900000-fe9fffff
        Prefetchable memory behind bridge: 00000000aff00000-00000000cfefffff
        Capabilities: <access denied>

00:09.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a4)
        Subsystem: ASUSTeK Computer Inc. Unknown device 815a
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: <access denied>

00:0a.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a4)
        Subsystem: ASUSTeK Computer Inc. K8N4-E Mainboard
        Flags: bus master, 66MHz, fast devsel, latency 0

00:0a.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
        Subsystem: ASUSTeK Computer Inc. K8N4-E Mainboard
        Flags: 66MHz, fast devsel, IRQ 10
        I/O ports at ec00 [size=32]
        I/O ports at 0600 [size=64]
        I/O ports at 0700 [size=64]
        Capabilities: <access denied>

00:0b.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2) (prog-if 10 [OHCI])
        Subsystem: ASUSTeK Computer Inc. K8N4-E Mainboard
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16
        Memory at febfe000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:0b.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a4) (prog-if 20 [EHCI])
        Subsystem: ASUSTeK Computer Inc. K8N4-E Mainboard
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 19
        Memory at febffc00 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:0d.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
        Subsystem: ASUSTeK Computer Inc. K8N4-E Mainboard
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16
        I/O ports at e400 [size=256]
        I/O ports at e000 [size=256]
        Memory at febfd000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:0f.0 IDE interface: nVidia Corporation CK804 IDE (rev f3) (prog-if 8a [Master SecP PriP])
        Subsystem: ASUSTeK Computer Inc. K8N4-E Mainboard
        Flags: bus master, 66MHz, fast devsel, latency 0
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
        I/O ports at ffa0 [size=16]
        Capabilities: <access denied>

00:10.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3) (prog-if 85 [Master SecO PriO])
        Subsystem: ASUSTeK Computer Inc. Unknown device 815a
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
        I/O ports at dc00 [size=8]
        I/O ports at d880 [size=4]
        I/O ports at d800 [size=8]
        I/O ports at d480 [size=4]
        I/O ports at d400 [size=16]
        Memory at febfc000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:12.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2) (prog-if 01 [Subtractive decode])
        Flags: bus master, 66MHz, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=05, sec-latency=64
        Memory behind bridge: fea00000-feafffff
        Prefetchable memory behind bridge: cff00000-dfefffff

00:13.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
        Subsystem: ASUSTeK Computer Inc. K8N4-E Mainboard
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17
        Memory at febfb000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at d080 [size=8]
        Capabilities: <access denied>

00:16.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
        Capabilities: <access denied>

00:17.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=07, subordinate=07, sec-latency=0
        Capabilities: <access denied>

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
        Flags: fast devsel
        Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
        Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
        Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
        Flags: fast devsel

01:00.0 RAID bus controller: Silicon Image, Inc. SiI 3132 Serial ATA Raid II Controller (rev 01)
        Subsystem: ASUSTeK Computer Inc. Unknown device 8177
        Flags: bus master, fast devsel, latency 0, IRQ 21
        Memory at fa7ffc00 (64-bit, non-prefetchable) [size=128]
        Memory at fa7f8000 (64-bit, non-prefetchable) [size=16K]
        I/O ports at ac00 [size=128]
        Expansion ROM at fa700000 [disabled] [size=512K]
        Capabilities: <access denied>

02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 15)
        Subsystem: ASUSTeK Computer Inc. Marvell 88E8053 Gigabit Ethernet controller PCIe (Asus)
        Flags: bus master, fast devsel, latency 0, IRQ 18
        Memory at fa8fc000 (64-bit, non-prefetchable) [size=16K]
        I/O ports at b800 [size=256]
        Expansion ROM at fa8c0000 [disabled] [size=128K]
        Capabilities: <access denied>

03:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GT] (rev a1) (prog-if 00 [VGA])
        Subsystem: eVga.com. Corp. Unknown device c553
        Flags: bus master, fast devsel, latency 0, IRQ 18
        Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
        Memory at b0000000 (64-bit, prefetchable) [size=256M]
        Memory at fc000000 (64-bit, non-prefetchable) [size=16M]
        I/O ports at cc00 [size=128]
        [virtual] Expansion ROM at fe9e0000 [disabled] [size=128K]
        Capabilities: <access denied>

04:06.0 PCI bridge: Pericom Semiconductor Unknown device 8140 (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=04, secondary=05, subordinate=05, sec-latency=64
        Prefetchable memory behind bridge: 00000000cff00000-00000000dfefffff
        Capabilities: <access denied>

04:08.0 Network controller: Broadcom Corporation BCM43XG (rev 01)
        Subsystem: Linksys Unknown device 0060
        Flags: bus master, fast devsel, latency 64, IRQ 10
        Memory at feafc000 (32-bit, non-prefetchable) [size=16K]

04:0b.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link) (prog-if 10 [OHCI])
        Subsystem: ASUSTeK Computer Inc. K8N4-E Mainboard
        Flags: bus master, medium devsel, latency 64, IRQ 18
        Memory at feafb800 (32-bit, non-prefetchable) [size=2K]
        Memory at feaf4000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

05:08.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
        Subsystem: Hauppauge computer works Inc. WinTV PVR 500 (1st unit)
        Flags: bus master, medium devsel, latency 64, IRQ 18
        Memory at d8000000 (32-bit, prefetchable) [size=64M]
        Capabilities: <access denied>

05:09.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
        Subsystem: Hauppauge computer works Inc. WinTV PVR 500 (2nd unit)
        Flags: bus master, medium devsel, latency 64, IRQ 21
        Memory at d4000000 (32-bit, prefetchable) [size=64M]
        Capabilities: <access denied>

```

It seems as if alsa itself is messed up.

---

