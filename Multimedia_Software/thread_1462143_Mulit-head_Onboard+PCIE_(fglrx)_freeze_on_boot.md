---
title: "Mulit-head Onboard+PCIE (fglrx) freeze on boot"
date: 2010-04-25
forum: Multimedia Software
---

### Post by jteutenberg on 2010-04-25
I'm trying to get a mulit-head setup working with two monitors, one run off an onboard Radeon 4200, the other of a Radeon 4350 PCIE card. However Ubuntu freezes while booting (I think the crash is when the second fglrx driver is loading). I can get a dual-head running off either card (one monitor using VGA and the other HDMI) without problems. 

The primary device is the onboard graphics (otherwise the bios won't enable it), and surround view is disabled (I've tried using surround view, and it fails in the same way). The driver is Catalyst Version 8.72.11, the motherboard is a Gigabyte GA-MA785GMT-UD2H.

Running it with a single head off the onboard graphics, lspci can see both devices:
```
01:05.0 VGA compatible controller: ATI Technologies Inc RS880 [Radeon HD 4200]
02:00.0 VGA compatible controller: ATI Technologies Inc RV710 [Radeon HD 4350]
```as can ati-config --lsa:
```
* 0. 01:05.0 ATI Radeon HD 4200
  1. 02:00.0 ATI Radeon HD 4300/4500 Series
```amdccle sees a Radeon HD 4200, and the other card is shown as an "Unknown adapter".

When I remove the old xorg.conf, run aticonfig --initial --adapter=all, and reboot, then the problems start.

I've looked at the Xorg.0.log file (I'm not sure what the appropriate logs to look at are), and the file ends part way through loading the driver for the PCIE card at:
```
...
(II) fglrx(1): VESA VBE OEM Product: RS880
(II) fglrx(1): VESA VBE OEM Product Rev: 01.00

```From looking at the loading of the onboard graphics (which has the same lines), the next line ought to be something like:
```
(II) fglrx(1): ATI Video BIOS revision 9 or later detected
```Any help is appreciated.

---

