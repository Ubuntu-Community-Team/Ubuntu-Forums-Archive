---
title: "No video on GeForce 8400GS with Intel 965 onboard"
date: 2009-02-20
forum: Multimedia Software
---

### Post by speedkreature on 2009-02-20
I've thrown together an oldish MSI barebones with G965 onboard video.  Added a GeForce 8400GS to the PCI slot in the riser card and installed Ubuntu 8.10 x86-32.
The install was quick with no problems aside from no video from the nvidia device.  I got a restricted modules popup asking me if I wanted to install driver 173 or 177 for the graphics card.  I selected 177, rebooted and...no dice.  The video is still on board, and I am dumped to the console after the screen flickers a couple times and reports no devices available.
I didn't grab any of the logs or xorg.conf files, and instead reinstalled.  This time I tried envyng (just for giggles).  The result was the same, except now I can get back to at least GUI after uninstalling the nvidia drivers.

My hope is to use dual monitors so I can multitask a little better but first I need to get video from the 8400GS.  I did grab the Xorg.0.log from the failed nvidia driver boot.  The only thing I see in it that is of any concern is that it sees two devices and doesn't seem to know what to do.

There s not option to disable the onboard video in BIOS, and I'm at a loss as to how to tell X.org which device to use.

---

### Post by speedkreature on 2009-02-20
I resolved this issue.  Simple A+ Cert. level stuff.  When a PC does not allow for selection of the boot video device but includes a PCIe x16 slot (whether on the mainboard or on a riser card) 9 times out of 10, it will auto-detect the x16 card and switch to that without any user intervention.  Not the case for a PCI graphics card, which is what I was using.  The catch here is that if the x16 slot is on a riser card, the slot that the riser card is plugged into has to be either a PCI-X (usually 64-bit @ 133MHz) or a PCI-e x16 slot.
 
I bought another 8400GS but x16 this time and it works perfectly.  Dual screens and all with no hassle.

---

