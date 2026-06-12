---
title: "Ubuntu 11.04 and VDPAU?"
date: 2011-08-01
forum: Multimedia Software
---

### Post by Muskiet on 2011-08-01
I just installed Ubuntu 11.04 (64 bit) on a system with a GeForce 210 graphics card and I can't get VDPAU to work.

Previously I ran 10.04 (32 bit) on the same system with SMPlayer working perfectly with VDPAU.
Now however if I select VDPAU in "preferences -> video -> output driver" there is no video, only sound.

---

### Post by Muskiet on 2011-08-01
Oh... I'm also running the "Experimental 3D Support for NVidia cards" driver in the "additional drivers" list which seems to be the only driver I found that runs properly on my system.

---

### Post by Muskiet on 2011-08-01
I've managed to get VDPAU working by installing VLC media player (not my favorite, but it works) and installing the VDPAU driver using:
```
sudo apt-get install vdpau-va-driver
```

I do like SMPlayer much better though so if someone has a tip on how to get that working it would be much appreciated.

---

### Post by BicyclerBoy on 2011-08-01
What you have working is VA-API with VLC..
The vdpau-va library is a VDPAU backend for VA-API.
I'm guessing that experimental 3d driver is nouveau & not nvidia driver.

The GT210 is very low power so needs the nvidia driver to work well.

Could examine or post your 
/var/log/Xorg.0,log
file as attachment (*.txt), this file will he;p debug the X server video driver

---

### Post by permagnus82 on 2011-11-28
Anyone had any progress on this post. I still have slow graphics, and sleep still don't work. I thought since there has been a while since any activity here, maybe someone did any better. 

I changed to ubunto from win 7 on this 1215b because it works smoother, and in win7 my touchpad was a mess, but it automaticly worked when installing ubuntu. I tried the 11.10 the day it was released but thought it was buggy then, so I'm back to 11.04.

---

