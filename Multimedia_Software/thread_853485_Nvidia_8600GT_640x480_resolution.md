---
title: "Nvidia 8600GT 640x480 resolution"
date: 2008-07-08
forum: Multimedia Software
---

### Post by agemon on 2008-07-08
hello, I have a Nvidia 8600GT and I'm running ubuntu 8.04. After I install the nvidia-glx-new package I can only change to the 640x480 or 320x240 resolutions... the hardware acceleration works (according to glxgears)

here's the xorg.conf file:
```

Section "InputDevice" 
Identifier "Generic Keyboard" 
Driver "kbd" 
Option "XkbRules" "xorg" 
Option "XkbModel" "pc105" 
Option "XkbLayout" "ro" 
EndSection 
 
Section "InputDevice" 
Identifier "Configured Mouse" 
Driver "mouse" 
Option "CorePointer" 
EndSection 
 
Section "Device" 
Identifier "Configured Video Device" 
EndSection 
 
Section "Monitor" 
Identifier "Configured Monitor" 
EndSection 
 
Section "Screen" 
Identifier "Default Screen" 
Monitor "Configured Monitor" 
Device "Configured Video Device" 
EndSection 
 
Section "ServerLayout" 
Identifier "Default Layout" 
Screen "Default Screen" 
EndSection

```
I searched the forums but I'm a little confused? Do I need to edit the xorg.config file, should I install envy?... Also, sudo dpkg-reconfigure -phigh xserver-xorg didn't work.
PS: this problem occurs on a friend's pc, so I'm a little hesitant to try all the solutions because he is the one who has to do the reboot (also I'm afraid of breaking something)

---

### Post by Nightbox on 2008-07-09
true, im his friend

when we enable the driver just low resolution

---

### Post by ad_267 on 2008-07-09
You should enable the drivers by going to System - Administration - Hardware Drivers, not by installing the nvidia-glx-new package.

Try running "gksudo nvidia-settings" and set up the resolution there.

---

### Post by Nightbox on 2008-07-09
already tried all

---

### Post by agemon on 2008-07-09
we tried adding
```

SubSection "Display"
Depth 16
Modes "1024x768"
EndSubSection
SubSection "Display"
Depth 24
Modes "1024x768"
EndSubSection

```
to xorg.conf but to no avail, when the nvidia module is load, the resolution is set to 640x480. Also, xrandr says that the only modes available are 640x480 and 320x240. Running `xrandr --fb (or --fbmm) 1024x768` didn't help either

---

### Post by xc3RnbFO8P on 2008-07-09
Did you try **Screens and Graphics** 
Application> other (if not)
System> Preferences> Main Menu> Other, check Screens and Graphics
Choose Generic

---

### Post by Nightbox on 2008-07-09
im trying

edit: worked but now the max resolution is 800x600

---

### Post by xc3RnbFO8P on 2008-07-09
Do you got Screen and Graphics in Application> other

---

### Post by Nightbox on 2008-07-09
i fixed, screens and graphics saved me, ty

---

### Post by sges on 2008-07-10
I had the same problem. My only solution was to run xfix to get vesa drivers and then run ENVYNG and manually chose the 96.43.05 drivers. Both the 169.xx.xx and 173.xx.xx put me in 640x480. I use Hardy x86-64 with nforce 430 (GeForce 6100 intergrated).

---

### Post by Chibana on 2008-07-10
This was a known problem with a new kernel for those of us with NVIDIA cards.  Mine has been broken ever since, even with every update that includes new kernel modules and the NVIDIA driver.  My thoughts were that they were continuing to try to fix it, and failing (at leas on my box).  Every time I install those updates, I have to reinstall the driver from NVIDIA, which works every time.  It's annoying as hell, though.  This really shouldn't be happening on on OS that is designed to take the bite out of Linux for "normal" users.

---

### Post by ad_267 on 2008-07-11
> **Chibana said:**
> This was a known problem with a new kernel for those of us with NVIDIA cards.  Mine has been broken ever since, even with every update that includes new kernel modules and the NVIDIA driver.  My thoughts were that they were continuing to try to fix it, and failing (at leas on my box).  Every time I install those updates, I have to reinstall the driver from NVIDIA, which works every time.  It's annoying as hell, though.  This really shouldn't be happening on on OS that is designed to take the bite out of Linux for "normal" users.

I haven't had any problems with my nvidia card, it's a 6600GT. And don't try and point the finger at Ubuntu, they can only work with what nvidia gives, which isn't much for Linux. I think my next video card will be an ATI now that they have open sourced their drivers, unless nvidia does the same.

---

### Post by sges on 2008-10-18
> **Chibana said:**
> This was a known problem with a new kernel for those of us with NVIDIA cards.  Mine has been broken ever since, even with every update that includes new kernel modules and the NVIDIA driver.  My thoughts were that they were continuing to try to fix it, and failing (at leas on my box).  Every time I install those updates, I have to reinstall the driver from NVIDIA, which works every time.  It's annoying as hell, though.  This really shouldn't be happening on on OS that is designed to take the bite out of Linux for "normal" users.

Kernel 2.6.24-21 seems to fix these problems.

---

