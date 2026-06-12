---
title: "problem when launching mame"
date: 2016-03-28
forum: Multimedia Software
---

### Post by harlock593 on 2016-03-28
hello,

i have an intel video card on my laptop but i think nvidia drivers are installed.

when i try to launch mame, i get this 

```
Xlib:  extension "NV-GLX" missing on display ":0.0".
Xlib:  extension "NV-GLX" missing on display ":0.0".
OpenGL not supported on this driver: Could not create GL context: BadValue (integer parameter out of range for operation)
video_init: Initialization failed!

```
lspci:
```
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation 7 Series Chipset Family LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57785 Gigabit Ethernet PCIe (rev 10)
02:00.1 SD Host controller: Broadcom Corporation BCM57765/57785 SDXC/MMC Card Reader (rev 10)
02:00.2 System peripheral: Broadcom Corporation BCM57765/57785 MS Card Reader (rev 10)
02:00.3 System peripheral: Broadcom Corporation BCM57765/57785 xD-Picture Card Reader (rev 10)
03:00.0 Network controller: Qualcomm Atheros AR9485 Wireless Network Adapter (rev 01)
```

what should i do next to make it work ?

same when i try to launch totem

---

