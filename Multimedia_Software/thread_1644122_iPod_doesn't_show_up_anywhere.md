---
title: "iPod doesn't show up anywhere"
date: 2010-12-12
forum: Multimedia Software
---

### Post by pr0grammer1 on 2010-12-12
I just bought a 4th-generation iPod Touch, and it shows up fine on my OSX laptop and Windows installation on this computer, but not under Ubuntu. I'm using the latest 10.10 build with all updates applied.


> alex@alex-desktop:~$ podsleuth
No iPods were found in the HAL device tree
Running dmesg gives me this (after unplugging the iPod and plugging it back in):
> [252551.337041] usb 1-6: USB disconnect, address 21
[252614.193768] usb 1-6: new high speed USB device using ehci_hcd and address 22
[252616.493775] usb 1-6: reset high speed USB device using ehci_hcd and address 22

I've tried all of the USB ports (including ones which work for other devices) and get the same results. The iPod doesn't show up in any program that I've tried (gparted, nautilus, RhythmBox, Amarok, Banshee).

Does anyone have any ideas? I'm kind of at a loss. :\

---

### Post by pr0grammer1 on 2010-12-16
Bump back from page 12.

---

