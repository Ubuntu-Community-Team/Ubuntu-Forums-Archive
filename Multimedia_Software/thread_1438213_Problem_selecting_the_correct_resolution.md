---
title: "Problem selecting the correct resolution"
date: 2010-03-24
forum: Multimedia Software
---

### Post by mysterian077 on 2010-03-24
I recently got a computer and installed the ubuntu 10.04 beta on it. I'm having issues getting my monitor to display at the correct resolution. It should be displaying at 1440x900, but the highest resolution I can select from the displays configuration panel is 1366x768, which is not even the correct aspect ratio. 

lspci:
```
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 12)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 12)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:16.2 IDE interface: Intel Corporation 5 Series/3400 Series Chipset PT IDER Controller (rev 06)
00:16.3 Serial controller: Intel Corporation 5 Series/3400 Series Chipset KT Controller (rev 06)
00:19.0 Ethernet controller: Intel Corporation 82578DC Gigabit Network Connection (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 06)
00:1c.6 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 7 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 IDE interface: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA IDE Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
00:1f.5 IDE interface: Intel Corporation 5 Series/3400 Series Chipset 2 port SATA IDE Controller (rev 06)

```
This is the whole thing, in case it helps.

From what I have read, this is a brand new chipset with the GPU built into the main CPU, as if it were another CPU core. Is there a driver for this yet, or do I have to deal with an improper resolution?

---

### Post by mysterian077 on 2010-03-25
UPDATE: So I've read elsewhere on the internet that this chipset and video card requires a newer build of the intel video driver than what comes in ubuntu. I should note that I'm using the 10.04 beta, as Karmic would not run on this PC.

apparently, the version I need is:
xf86-video-intel-2.10.0-r1, and the newest version from the ubuntu repo is 2.9.1-ubuntu1

---

