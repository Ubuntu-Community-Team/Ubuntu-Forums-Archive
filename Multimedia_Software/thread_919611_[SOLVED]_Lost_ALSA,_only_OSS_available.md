---
title: "[SOLVED] Lost ALSA, only OSS available"
date: 2008-09-14
forum: Multimedia Software
---

### Post by peruvianfreak250 on 2008-09-14
ok guys, so i feel stupid because i think i somehow disabled alsa in my computer. I was trying to figure out a way to make teamspeak work on my computer and after a long time, i guess i accidentally did something that has disabled my alsa. Now in Volume control i only see Analog Devices:AD1988 (OSS mixer), there used to be like 10 choices in there. Is there anything i can do to access ALSA again?:(

here is lspci
> 
00:00.0 Host bridge: ATI Technologies Inc RD580 [CrossFire Xpress 3200] Chipset Host Bridge
00:02.0 PCI bridge: ATI Technologies Inc RS480 PCI-X Root Port
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 13)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon HD 2400 XT
01:00.1 Audio device: ATI Technologies Inc RV610 audio device [Radeon HD 2400 PRO]
02:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
03:01.0 Network controller: RaLink Unknown device 0601
03:03.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0)
03:04.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)

---

### Post by nalmeth on 2008-09-14
What happens when you do the following?
```
sudo /etc/init.d/alsa-utils restart
```

---

### Post by peruvianfreak250 on 2008-09-15
i get this

> amixer: Mixer attach hw:0 error: Invalid argument
ALSA lib conf.c:1589:(snd_config_load1) _toplevel_:48:32:Unexpected char
ALSA lib conf.c:2850:(snd_config_hook_load) /etc/asound.conf may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2714:(snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3079:(snd_config_update_r) hooks failed, removing configuration
amixer: Mixer attach hw:0 error: Invalid argument
ALSA lib conf.c:1589: (snd_config_load1) _toplevel_:48:32:Unexpected char
ALSA lib conf.c:2850: (snd_config_hook_load) /etc/asound.conf may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2714: (snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3079: (snd_config_update_r) hooks failed, removing configuration
amixer: Mixer attach hw:0 error: Invalid argument
ALSA lib conf.c:1589: (snd_config_load1) _toplevel_:48:32:Unexpected char
ALSA lib conf.c:2850: (snd_config_hook_load) /etc/asound.conf may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2714: (snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3079: (snd_config_update_r) hooks failed, removing configuration
amixer: Mixer attach hw:0 error: Invalid argument
ALSA lib conf.c:1589: (snd_config_load1) _toplevel_:48:32:Unexpected char
ALSA lib conf.c:2850: (snd_config_hook_load) /etc/asound.conf may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2714: (snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3079: (snd_config_update_r) hooks failed, removing configuration
amixer: Mixer attach hw:0 error: Invalid argument
ALSA lib conf.c:1589: (snd_config_load1) _toplevel_:48:32:Unexpected char
ALSA lib conf.c:2850: (snd_config_hook_load) /etc/asound.conf may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2714: (snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3079: (snd_config_update_r) hooks failed, removing configuration
amixer: Mixer attach hw: 0 error: Invalid argument
ALSA lib conf.c:1589: (snd_config_load1) _toplevel_:48:32:Unexpected char
ALSA lib conf.c:2850: (snd_config_hook_load) /etc/asound.conf may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2714: (snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3079: (snd_config_update_r) hooks failed, removing configuration
amixer: Mixer attach hw: 0 error: Invalid argument
ALSA lib conf.c:1589: (snd_config_load1) _toplevel_:48:32:Unexpected char
ALSA lib conf.c:2850: (snd_config_hook_load) /etc/asound.conf may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2714: (snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3079: (snd_config_update_r) hooks failed, removing configuration
amixer: Mixer attach hw: 0 error: Invalid argument
ALSA lib conf.c:1589: (snd_config_load1) _toplevel_:48:32:Unexpected char
ALSA lib conf.c:2850: (snd_config_hook_load) /etc/asound.conf may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2714: (snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3079: (snd_config_update_r) hooks failed, removing configuration
amixer: Mixer attach hw: 0 error: Invalid argument
ALSA lib conf.c:1589: (snd_config_load1) _toplevel_:48:32:Unexpected char
ALSA lib conf.c:2850: (snd_config_hook_load) /etc/asound.conf may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2714: (snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3079: (snd_config_update_r) hooks failed, removing configuration
amixer: Mixer attach hw: 0 error: Invalid argument
ALSA lib conf.c:1589: (snd_config_load1) _toplevel_:48:32:Unexpected char
ALSA lib conf.c:2850: (snd_config_hook_load) /etc/asound.conf may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2714: (snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3079: (snd_config_update_r) hooks failed, removing configuration
amixer: Mixer attach hw:0 error: Invalid argument
ALSA lib conf.c:1589: (snd_config_load1) _toplevel_:48:32:Unexpected char
ALSA lib conf.c:2850: (snd_config_hook_load) /etc/asound.conf may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2714: (snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3079: (snd_config_update_r) hooks failed, removing configuration
amixer: Mixer attach hw:0 error: Invalid argument
ALSA lib conf.c:1589: (snd_config_load1) _toplevel_:48:32:Unexpected char
ALSA lib conf.c:2850: (snd_config_hook_load) /etc/asound.conf may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2714: (snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3079: (snd_config_update_r) hooks failed, removing configuration
amixer: Mixer attach hw:0 error: Invalid argument
ALSA lib conf.c:1589: (snd_config_load1) _toplevel_:48:32:Unexpected char
ALSA lib conf.c:2850: (snd_config_hook_load) /etc/asound.conf may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2714: (snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3079: (snd_config_update_r) hooks failed, removing configuration
amixer: Mixer attach hw:0 error: Invalid argument
ALSA lib conf.c:1589: (snd_config_load1) _toplevel_:48:32:Unexpected char
ALSA lib conf.c:2850: (snd_config_hook_load) /etc/asound.conf may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2714: (snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3079: (snd_config_update_r) hooks failed, removing configuration
amixer: Mixer attach hw:0 error: Invalid argument
ALSA lib conf.c:1589: (snd_config_load1) _toplevel_:48:32:Unexpected char
ALSA lib conf.c:2850: (snd_config_hook_load) /etc/asound.conf may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2714: (snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3079: (snd_config_update_r) hooks failed, removing configuration
amixer: Mixer attach hw:0 error: Invalid argument
ALSA lib conf.c:1589: (snd_config_load1) _toplevel_:48:32:Unexpected char
ALSA lib conf.c:2850: (snd_config_hook_load) /etc/asound.conf may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2714: (snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3079: (snd_config_update_r) hooks failed, removing configuration
amixer: Mixer attach hw:0 error: Invalid argument
ALSA lib conf.c:1589: (snd_config_load1) _toplevel_:48:32:Unexpected char
ALSA lib conf.c:2850: (snd_config_hook_load) /etc/asound.conf may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2714: (snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3079: (snd_config_update_r) hooks failed, removing configuration
amixer: Mixer attach hw: 0 error: Invalid argument
ALSA lib conf.c:1589: (snd_config_load1) _toplevel_:48:32:Unexpected char
ALSA lib conf.c:2850: (snd_config_hook_load) /etc/asound.conf may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2714: (snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3079: (snd_config_update_r) hooks failed, removing configuration
amixer: Mixer attach hw: 0 error: Invalid argument
ALSA lib conf.c:1589: (snd_config_load1) _toplevel_:48:32:Unexpected char
ALSA lib conf.c:2850: (snd_config_hook_load) /etc/asound.conf may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2714: (snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3079: (snd_config_update_r) hooks failed, removing configuration
amixer: Mixer attach hw: 0 error: Invalid argument
ALSA lib conf.c:1589: (snd_config_load1) _toplevel_:48:32:Unexpected char
ALSA lib conf.c:2850: (snd_config_hook_load) /etc/asound.conf may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2714: (snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3079: (snd_config_update_r) hooks failed, removing configuration
amixer: Mixer attach hw:0 error: Invalid argument
ALSA lib conf.c:1589: (snd_config_load1) _toplevel_:48:32:Unexpected char
ALSA lib conf.c:2850: (snd_config_hook_load) /etc/asound.conf may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2714: (snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3079: (snd_config_update_r) hooks failed, removing configuration
amixer: Mixer attach hw:0 error: Invalid argument
ALSA lib conf.c:1589: (snd_config_load1) _toplevel_:48:32:Unexpected char
ALSA lib conf.c:2850: (snd_config_hook_load) /etc/asound.conf may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2714: (snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3079: (snd_config_update_r) hooks failed, removing configuration
amixer: Mixer attach hw:0 error: Invalid argument
ALSA lib conf.c:1589: (snd_config_load1) _toplevel_:48:32:Unexpected char
ALSA lib conf.c:2850: (snd_config_hook_load) /etc/asound.conf may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2714: (snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3079: (snd_config_update_r) hooks failed, removing configuration
amixer: Mixer attach hw: 0 error: Invalid argument
ALSA lib conf.c:1589: (snd_config_load1) _toplevel_:48:32:Unexpected char
ALSA lib conf.c:2850: (snd_config_hook_load) /etc/asound.conf may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2714: (snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3079: (snd_config_update_r) hooks failed, removing configuration
amixer: Mixer attach hw:0 error: Invalid argument
ALSA lib conf.c:1589: (snd_config_load1) _toplevel_:48:32:Unexpected char
ALSA lib conf.c:2850: (snd_config_hook_load) /etc/asound.conf may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2714: (snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3079: (snd_config_update_r) hooks failed, removing configuration
amixer: Mixer attach hw: 0 error: Invalid argument
ALSA lib conf.c:1589: (snd_config_load1) _toplevel_:48:32:Unexpected char
ALSA lib conf.c:2850: (snd_config_hook_load) /etc/asound.conf may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2714: (snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3079: (snd_config_update_r) hooks failed, removing configuration
amixer: Mixer attach hw: 0 error: Invalid argument
ALSA lib conf.c:1589: (snd_config_load1) _toplevel_:48:32:Unexpected char
ALSA lib conf.c:2850: (snd_config_hook_load) /etc/asound.conf may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2714: (snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3079: (snd_config_update_r) hooks failed, removing configuration
amixer: Mixer attach hw:0 error: Invalid argument
ALSA lib conf.c:1589: (snd_config_load1) _toplevel_:48:32:Unexpected char
ALSA lib conf.c:2850: (snd_config_hook_load) /etc/asound.conf may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2714: (snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3079: (snd_config_update_r) hooks failed, removing configuration
amixer: Mixer attach hw:0 error: Invalid argument
ALSA lib conf.c:1589: (snd_config_load1) _toplevel_:48:32:Unexpected char
ALSA lib conf.c:2850: (snd_config_hook_load) /etc/asound.conf may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2714: (snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3079: (snd_config_update_r) hooks failed, removing configuration
amixer: Mixer attach hw: 0 error: Invalid argument
ALSA lib conf.c:1589: (snd_config_load1) _toplevel_:48:32:Unexpected char
ALSA lib conf.c:2850: (snd_config_hook_load) /etc/asound.conf may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2714: (snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3079: (snd_config_update_r) hooks failed, removing configuration
amixer: Mixer attach hw: 0 error: Invalid argument
ALSA lib conf.c:1589: (snd_config_load1) _toplevel_:48:32:Unexpected char
ALSA lib conf.c:2850: (snd_config_hook_load) /etc/asound.conf may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2714: (snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3079: (snd_config_update_r) hooks failed, removing configuration
amixer: Mixer attach hw: 0 error: Invalid argument
ALSA lib conf.c:1589: (snd_config_load1) _toplevel_:48:32:Unexpected char
ALSA lib conf.c:2850: (snd_config_hook_load) /etc/asound.conf may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2714: (snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3079: (snd_config_update_r) hooks failed, removing configuration
amixer: Mixer attach hw: 0 error: Invalid argument
ALSA lib conf.c:1589: (snd_config_load1) _toplevel_:48:32:Unexpected char
ALSA lib conf.c:2850: (snd_config_hook_load) /etc/asound.conf may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2714: (snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3079: (snd_config_update_r) hooks failed, removing configuration
amixer: Mixer attach hw: 0 error: Invalid argument
ALSA lib conf.c:1589: (snd_config_load1) _toplevel_:48:32:Unexpected char
ALSA lib conf.c:2850: (snd_config_hook_load) /etc/asound.conf may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2714: (snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3079: (snd_config_update_r) hooks failed, removing configuration
amixer: Mixer attach hw: 0 error: Invalid argument
ALSA lib conf.c:1589: (snd_config_load1) _toplevel_:48:32:Unexpected char
ALSA lib conf.c:2850: (snd_config_hook_load) /etc/asound.conf may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2714: (snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3079: (snd_config_update_r) hooks failed, removing configuration
amixer: Mixer attach hw: 0 error: Invalid argument
ALSA lib conf.c:1589: (snd_config_load1) _toplevel_:48:32:Unexpected char
ALSA lib conf.c:2850: (snd_config_hook_load) /etc/asound.conf may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2714: (snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3079: (snd_config_update_r) hooks failed, removing configuration
amixer: Mixer attach hw:1 error: Invalid argument
ALSA lib conf.c:1589: (snd_config_load1) _toplevel_:48:32:Unexpected char
ALSA lib conf.c:2850: (snd_config_hook_load) /etc/asound.conf may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2714: (snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3079: (snd_config_update_r) hooks failed, removing configuration
amixer: Mixer attach hw:1 error: Invalid argument
ALSA lib conf.c:1589: (snd_config_load1) _toplevel_:48:32:Unexpected char
ALSA lib conf.c:2850: (snd_config_hook_load) /etc/asound.conf may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2714: (snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3079: (snd_config_update_r) hooks failed, removing configuration
amixer: Mixer attach hw:1 error: Invalid argument
ALSA lib conf.c:1589: (snd_config_load1) _toplevel_:48:32:Unexpected char
ALSA lib conf.c:2850: (snd_config_hook_load) /etc/asound.conf may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2714: (snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3079: (snd_config_update_r) hooks failed, removing configuration
amixer: Mixer attach hw:1 error: Invalid argument
ALSA lib conf.c:1589: (snd_config_load1) _toplevel_:48:32:Unexpected char
ALSA lib conf.c:2850: (snd_config_hook_load) /etc/asound.conf may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2714: (snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3079: (snd_config_update_r) hooks failed, removing configuration
amixer: Mixer attach hw:1 error: Invalid argument
ALSA lib conf.c:1589: (snd_config_load1) _toplevel_:48:32:Unexpected char
ALSA lib conf.c:2850: (snd_config_hook_load) /etc/asound.conf may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2714: (snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3079: (snd_config_update_r) hooks failed, removing configuration
amixer: Mixer attach hw:1 error: Invalid argument
ALSA lib conf.c:1589: (snd_config_load1) _toplevel_:48:32:Unexpected char
ALSA lib conf.c:2850: (snd_config_hook_load) /etc/asound.conf may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2714: (snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3079: (snd_config_update_r) hooks failed, removing configuration
amixer: Mixer attach hw: 1 error: Invalid argument
ALSA lib conf.c:1589: (snd_config_load1) _toplevel_:48:32:Unexpected char
ALSA lib conf.c:2850: (snd_config_hook_load) /etc/asound.conf may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2714: (snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3079: (snd_config_update_r) hooks failed, removing configuration
amixer: Mixer attach hw:1 error: Invalid argument
ALSA lib conf.c:1589: (snd_config_load1) _toplevel_:48:32:Unexpected char
ALSA lib conf.c:2850: (snd_config_hook_load) /etc/asound.conf may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2714: (snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3079: (snd_config_update_r) hooks failed, removing configuration
amixer: Mixer attach hw:1 error: Invalid argument
ALSA lib conf.c:1589: (snd_config_load1) _toplevel_:48:32:Unexpected char
ALSA lib conf.c:2850: (snd_config_hook_load) /etc/asound.conf may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2714: (snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3079: (snd_config_update_r) hooks failed, removing configuration
amixer: Mixer attach hw:1 error: Invalid argument
ALSA lib conf.c:1589: (snd_config_load1) _toplevel_:48:32:Unexpected char
ALSA lib conf.c:2850: (snd_config_hook_load) /etc/asound.conf may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2714: (snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3079: (snd_config_update_r) hooks failed, removing configuration
amixer: Mixer attach hw:1 error: Invalid argument
ALSA lib conf.c:1589: (snd_config_load1) _toplevel_:48:32:Unexpected char
ALSA lib conf.c:2850: (snd_config_hook_load) /etc/asound.conf may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2714: (snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3079: (snd_config_update_r) hooks failed, removing configuration
amixer: Mixer attach hw:1 error: Invalid argument
ALSA lib conf.c:1589: (snd_config_load1) _toplevel_:48:32:Unexpected char
ALSA lib conf.c:2850: (snd_config_hook_load) /etc/asound.conf may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2714: (snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3079: (snd_config_update_r) hooks failed, removing configuration
amixer: Mixer attach hw:1 error: Invalid argument
ALSA lib conf.c:1589: (snd_config_load1) _toplevel_:48:32:Unexpected char
ALSA lib conf.c:2850: (snd_config_hook_load) /etc/asound.conf may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2714: (snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3079: (snd_config_update_r) hooks failed, removing configuration
amixer: Mixer attach hw:1 error: Invalid argument
ALSA lib conf.c:1589: (snd_config_load1) _toplevel_:48:32:Unexpected char
ALSA lib conf.c:2850: (snd_config_hook_load) /etc/asound.conf may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2714: (snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3079: (snd_config_update_r) hooks failed, removing configuration
amixer: Mixer attach hw:1 error: Invalid argument
ALSA lib conf.c:1589: (snd_config_load1) _toplevel_:48:32:Unexpected char
ALSA lib conf.c:2850: (snd_config_hook_load) /etc/asound.conf may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2714: (snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3079: (snd_config_update_r) hooks failed, removing configuration
amixer: Mixer attach hw:1 error: Invalid argument
ALSA lib conf.c:1589: (snd_config_load1) _toplevel_:48:32:Unexpected char
ALSA lib conf.c:2850: (snd_config_hook_load) /etc/asound.conf may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2714: (snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3079: (snd_config_update_r) hooks failed, removing configuration
amixer: Mixer attach hw:1 error: Invalid argument
ALSA lib conf.c:1589: (snd_config_load1) _toplevel_:48:32:Unexpected char
ALSA lib conf.c:2850: (snd_config_hook_load) /etc/asound.conf may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2714: (snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3079: (snd_config_update_r) hooks failed, removing configuration
amixer: Mixer attach hw:1 error: Invalid argument
ALSA lib conf.c:1589: (snd_config_load1) _toplevel_:48:32:Unexpected char
ALSA lib conf.c:2850: (snd_config_hook_load) /etc/asound.conf may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2714: (snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3079: (snd_config_update_r) hooks failed, removing configuration
amixer: Mixer attach hw:1 error: Invalid argument
ALSA lib conf.c:1589: (snd_config_load1) _toplevel_:48:32:Unexpected char
ALSA lib conf.c:2850: (snd_config_hook_load) /etc/asound.conf may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2714: (snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3079: (snd_config_update_r) hooks failed, removing configuration
amixer: Mixer attach hw:1 error: Invalid argument
ALSA lib conf.c:1589: (snd_config_load1) _toplevel_:48:32:Unexpected char
ALSA lib conf.c:2850: (snd_config_hook_load) /etc/asound.conf may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2714: (snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3079: (snd_config_update_r) hooks failed, removing configuration 
amixer: Mixer attach hw:1 error: Invalid argument
ALSA lib conf.c:1589: (snd_config_load1) _toplevel_:48:32:Unexpected char
ALSA lib conf.c:2850: (snd_config_hook_load) /etc/asound.conf may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2714: (snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3079: (snd_config_update_r) hooks failed, removing configuration
amixer: Mixer attach hw:1 error: Invalid argument
ALSA lib conf.c:1589: (snd_config_load1) _toplevel_:48:32:Unexpected char
ALSA lib conf.c:2850: (snd_config_hook_load) /etc/asound.conf may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2714: (snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3079: (snd_config_update_r) hooks failed, removing configuration
amixer: Mixer attach hw:1 error: Invalid argument
ALSA lib conf.c:1589: (snd_config_load1) _toplevel_:48:32:Unexpected char
ALSA lib conf.c:2850: (snd_config_hook_load) /etc/asound.conf may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2714: (snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3079: (snd_config_update_r) hooks failed, removing configuration
amixer: Mixer attach hw:1 error: Invalid argument
ALSA lib conf.c:1589: (snd_config_load1) _toplevel_:48:32:Unexpected char
ALSA lib conf.c:2850: (snd_config_hook_load) /etc/asound.conf may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2714: (snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3079: (snd_config_update_r) hooks failed, removing configuration
amixer: Mixer attach hw:1 error: Invalid argument
ALSA lib conf.c:1589: (snd_config_load1) _toplevel_:48:32:Unexpected char
ALSA lib conf.c:2850: (snd_config_hook_load) /etc/asound.conf may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2714: (snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3079: (snd_config_update_r) hooks failed, removing configuration
amixer: Mixer attach hw:1 error: Invalid argument
ALSA lib conf.c:1589: (snd_config_load1) _toplevel_:48:32:Unexpected char
ALSA lib conf.c:2850: (snd_config_hook_load) /etc/asound.conf may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2714: (snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3079: (snd_config_update_r) hooks failed, removing configuration
amixer: Mixer attach hw:1 error: Invalid argument
ALSA lib conf.c:1589: (snd_config_load1) _toplevel_:48:32:Unexpected char
ALSA lib conf.c:2850: (snd_config_hook_load) /etc/asound.conf may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2714: (snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3079: (snd_config_update_r) hooks failed, removing configuration
amixer: Mixer attach hw:1 error: Invalid argument
ALSA lib conf.c:1589: (snd_config_load1) _toplevel_:48:32:Unexpected char
ALSA lib conf.c:2850: (snd_config_hook_load) /etc/asound.conf may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2714: (snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3079: (snd_config_update_r) hooks failed, removing configuration
amixer: Mixer attach hw:1 error: Invalid argument
ALSA lib conf.c:1589: (snd_config_load1) _toplevel_:48:32:Unexpected char
ALSA lib conf.c:2850: (snd_config_hook_load) /etc/asound.conf may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2714: (snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3079: (snd_config_update_r) hooks failed, removing configuration
amixer: Mixer attach hw:1 error: Invalid argument
ALSA lib conf.c:1589: (snd_config_load1) _toplevel_:48:32:Unexpected char
ALSA lib conf.c:2850: (snd_config_hook_load) /etc/asound.conf may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2714: (snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3079: (snd_config_update_r) hooks failed, removing configuration
amixer: Mixer attach hw:1 error: Invalid argument
ALSA lib conf.c:1589: (snd_config_load1) _toplevel_:48:32:Unexpected char
ALSA lib conf.c:2850: (snd_config_hook_load) /etc/asound.conf may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2714: (snd_config_hooks_call) function snd_config_hook_load  returned error: Invalid argument
ALSA lib conf.c:3079: (snd_config_update_r) hooks failed, removing configuration
amixer: Mixer attach hw:1 error: Invalid argument
ALSA lib conf.c:1589: (snd_config_load1) _toplevel_:48:32:Unexpected char
ALSA lib conf.c:2850: (snd_config_hook_load) /etc/asound.conf may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2714: (snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3079: (snd_config_update_r) hooks failed, removing configuration
amixer: Mixer attach hw:1 error: Invalid argument
ALSA lib conf.c:1589: (snd_config_load1) _toplevel_:48:32:Unexpected char
ALSA lib conf.c:2850: (snd_config_hook_load) /etc/asound.conf may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2714: (snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3079: (snd_config_update_r) hooks failed, removing configuration
amixer: Mixer attach hw:1 error: Invalid argument
ALSA lib conf.c:1589: (snd_config_load1) _toplevel_:48:32:Unexpected char
ALSA lib conf.c:2850: (snd_config_hook_load) /etc/asound.conf may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2714: (snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3079: (snd_config_update_r) hooks failed, removing configuration
amixer: Mixer attach hw:1 error: Invalid argument
ALSA lib conf.c:1589: (snd_config_load1) _toplevel_:48:32:Unexpected char
ALSA lib conf.c:2850: (snd_config_hook_load) /etc/asound.conf may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2714: (snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3079: (snd_config_update_r) hooks failed, removing configuration
amixer: Mixer attach hw:1 error: Invalid argument

---

### Post by peruvianfreak250 on 2008-09-15
oh thank you man, i was looking at this thing and i saw that it said that my asound.conf may be bad. and i remembered that i had created this file to try to tweak my sound. so i deleted it and restarted my alsa. now i have 2 alsa devices and a oss device but i used to have like 8 off them, pulseaudio and stuff like that. anyone know how to get all my audio devices back?

---

### Post by markbuntu on 2008-09-16
You should sheck in System/Administration/Services/ and make sure that alsa-utils are running and in System/Preferences/Session/Startup Programs that Pulseaudio Device Chooser is running. You should also check that you have sound mixing enabled in System/Preferences/Sound/Sounds.

You can also read my guide, it will tell you how to basically reset your sound and get everything working again:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by peruvianfreak250 on 2008-09-23
thanks man, this got it :)

---

