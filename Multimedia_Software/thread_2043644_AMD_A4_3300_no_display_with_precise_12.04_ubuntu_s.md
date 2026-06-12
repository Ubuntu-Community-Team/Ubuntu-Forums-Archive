---
title: "AMD A4 3300 no display with precise 12.04 ubuntu server"
date: 2012-08-17
forum: Multimedia Software
---

### Post by i like beer on 2012-08-17
I know this is a known issue, but I just want to spell out the exact issue.

AMD A4 3300 APU.

After install of Ubuntu-Server 12.04 (on first boot) - no video after grub menu (monitor goes into standby).

Boot from ubuntu-desktop 12.04 DVD, monitor in standby.

Same with USB stick boot, monitor in standby.

ie: no way to get a working screen with this APU.

Boot into recovery mode from ubuntu-server 12.04 (installed), the monitor will work (ie: not in standby).

Install nvidia 7200 PCI-e card into server after install, no problems with anything.

Is there going to be a fix for the AMD A4 3300 APU? I can install the proprietary driver and it will work of course but I do not want my server to break with the next kernel upgrade.

All I want is a basic graphical console with the AMD A4 3300 APU. Hardware acceleration would be nice though :D

cheers

---

### Post by Yellow Orange on 2012-08-21
Hello!

I've bought the same CPU today for an entry-level file server and had the same problem.

You have to uncomment
```
GRUB_TERMINAL=console
```
, set the fixed resolution (you can use any resolution what supported by your screen)
```
GRUB_GFXMODE=800x600
```
into **/etc/default/grub** and update grub.cfg
```
# update-grub
```

P.S. 
> All I want is a basic graphical console with the AMD A4 3300 APU. Hardware acceleration would be nice though 
I have **not** install X and I can't tell anything about it in this case, but I think it's going to start without problem.

---

### Post by QIII on 2012-08-21
The driver will not break on kernel updates if you install it from the repo using the "Using the Ubuntu repositories (alternate command line method)" detailed in the ATI driver wiki in my signature.

---

### Post by fudoki on 2012-08-23
> **Yellow Orange said:**
> Hello!

I've bought the same CPU today for an entry-level file server and had the same problem.

You have to uncomment
```
GRUB_TERMINAL=console
```
, set the fixed resolution (you can use any resolution what supported by your screen)
```
GRUB_GFXMODE=800x600
```
into **/etc/default/grub** and update grub.cfg
```
# update-grub
```

P.S. 

I have **not** install X and I can't tell anything about it in this case, but I think it's going to start without problem.

Would love to try your suggestion, but since I have NO DISPLAY WHATSOEVER NOW (monitor just blinks "Out of Range", when I substitute a $2,500 NEC Multi-Sync it reports "Out of Range").  One must wonder what Grub is having my Nvidia 7600GT output if the NEC, and also a Sony Multi-Sync CRT won't handle the signal - but they DO only go up to 100kHz...

This is the third version of Ubuntu where I have gone through the install right up to "showtime", only to have the display become unusable.  Will I switch back to Debian again - since it always works.  Is the Unity interface really worth it?

Is there a FILE in Grub that I can edit with, say, Puppy Linux that will allow Ubuntu to actually have some display output?

Any help of this sort would be greatly appreciated!

---

### Post by fudoki on 2012-08-23
Don't worry about a response.  Have installed Linux Mint Debian Edition.  Decided that this was the third, and last, time I would go through a complete Ubuntu install, upgrades, and after applying the upgrades being faced with a system with no display.

Have had no problems installing on 5 generic, "WalMart" machines, but when I installed it on my personal box AMD9950 X4, Asus M3A-H/HDMI motherboard w/Nvidia 7600GT video card and 8Gb DRAM I wind up with no display.

My guess is the kernel update in the 384 files that had to be upgraded was flawed, and the init file that was generated is a dead letter.

Adios Ubuntu for my personal machine.  It's good eye candy but I needed to be back in production this morning...
Debian works.

---

### Post by Yellow Orange on 2012-08-23
> Would love to try your suggestion, but since I have NO DISPLAY WHATSOEVER NOW
](*,) I did it in the recovery mode. It's available in the grub menu.

---

