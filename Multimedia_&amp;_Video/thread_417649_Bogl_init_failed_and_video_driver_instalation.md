---
title: "Bogl_init failed and video driver instalation"
date: 2007-04-21
forum: Multimedia &amp; Video
---

### Post by ferpadro on 2007-04-21
This message appears on screen seconds later i decide to reboot/turn off my computer from feisty:

"bogl_init failed: reading screen info: inapropiate ioctl for devices. Screen init failed"

The screen doesnt freeze. In fact it turns off without any major problems, but i wanna be sure this isnt affecting any other part of my ubuntu. Any ideas on how to solve this?

Another this is, i installed my Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter with $sudo dpkg-reconfigure xserver-xorg and i noticed a great improvement in window scrolling and video playing, but i wanna know if i have my drivers working 100% or if there is another way of installing them.

This is the result of lspci command and the content of the media section in the xorg.conf file:


lspci:

00:00.0 Host bridge: Silicon Integrated Systems [SiS] 651 Host (rev 02)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS962 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:10.0 Communication controller: Motorola Wildcard X100P
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter

xorg.conf (video section):

Section "Device"
    Identifier    "Generic Video Card"
    Driver        "sis"
    BusID        "PCI:1:0:0"
    Option        "UseFBDev"        "true"
EndSection

Section "Monitor"
    Identifier    "Samsung 793v"
    Option        "DPMS"
    HorizSync    30-70
    VertRefresh    50-160
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "Generic video card"
    Monitor        "Samsung 793v"
    DefaultDepth    24
    SubSection "Display"

 Thanks in advance!!!

---

### Post by ferpadro on 2007-04-22
bump, plz help me ;_;

---

### Post by ferpadro on 2007-04-22
bump #2

---

### Post by Oklin on 2007-04-24
Ahh, finally someone with the same graphic card as mine.

I hope you can help me install it.

I have been looking around on a lot of forums, and asked different places with no luck.

And i see that you have installed it with xserver-xorg, I never runned that program, but i can see i have it installed, so i tried to use it, but there was a lot of questions that i wasnt sure what to answer.

I havent been able to find a guide for the graphic card, so i dont know what to choose in the xserver-xorg, can you help me through it step by step?

I'm sorry i can't help you with your problem, but i hope you can help me with mine. Cuz i really cant find anyone else with that graphic card.

---

### Post by algamest on 2007-04-26
oklin -- run: 

```
 sudo dpkg-reconfigure xserver-xorg 
```

And make sure to choose "SiS" as your driver.  This will allow you to (theoretically) take advantage of hardware acceleration, and will also allow for smoother/faster desktop display, and higher resolutions ( above 1024x768 ).  

Anyway, I'm also having the "bogl_init failed: reading screen info: inapropiate ioctl for devices. Screen init failed" issue on system shutdown.  I'm also having trouble running compiz/beryl ( expected, as I doubt SiS support is built into it ), and 3-D acceleration is abysmal.  This is also to be expected, as from what I gather, this series of SiS cards isn't particularly powerful.  But you'd think I'd be able to get more than 1 FPS on some of the basic 3-D games provided through Synaptic (e.g., Neverball).

My lspci and xorg.conf are similar to ferpadro's as well.

This isn't a crucial issue, I suppose, but any help would be very much appreciated, as I'd like to utilize the full potential of my laptop ( Acer Aspire 3004 WLCi ) under Ubuntu.

Thanks in advance!

---

### Post by Oklin on 2007-04-26
> **algamest said:**
> oklin -- run: 

```
 sudo dpkg-reconfigure xserver-xorg 
```

And make sure to choose "SiS" as your driver.  This will allow you to (theoretically) take advantage of hardware acceleration, and will also allow for smoother/faster desktop display, and higher resolutions ( above 1024x768 ).  


thanks for the reply..

i did that, and picked SiS, after that a lot of other configurenges comes up, does any of those have anything to do with my graphic card?

---

### Post by algamest on 2007-04-28
No, defaults should be fine, unless Linux has drivers for your monitor.  I know there's a thread on this forum that has far more detailed instructions on how to set this up... a Google search should turn up some results as well... that's how I fixed it.

So, noone has any advice for the issue this thread was originally opened for?

---

### Post by algamest on 2007-05-02
No advice from anyone?  No one else has encountered this situation?

---

### Post by bakermiller on 2007-05-02
i'm in the same spot. 
can't get beryl to work. 
When i even slightly ask for some 3d rendering, the computer crashes!!! 
I got to play some armagetron though!!! don't know how...

i can't even get the desktop effects to work, the computer just goes blank.
I tried a glx-gnome session and all i got was noise and fuzz and strange distorted windows. scary...

i have pretty much the same xorg.conf graphics settings as above, but i'm set-up with dual-monitors.

Acer aspire 5000.
 I guess i have the SiS card too (661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter). is that the graphics card?? i thought it was my monitor!?

I have no idea what to do. stuck.

---

### Post by lxop on 2007-05-16
Just put my 2 cents in to say I have the shutdown message problem too, and would like to know if there is anything that can be done about it
Cheers

---

### Post by peterx14 on 2007-06-29
..and another one! This is on a Packard Bell iGo 4450 (aka NEC Versa E400). Otherwise though, the machine runs fine; the error message on shutdown just bugs me a little!

---

### Post by furumaro on 2007-08-08
Had the same error message and no shutdown splash. Adding vga=791 to the kernel-line in my /boot/grub/menu.lst resolved the problem.

My kernel-line now looks like this:
kernel		/boot/vmlinuz-2.6.20-16-generic root=/dev/hda4 ro vga=791 quiet splash

The value 791 could be different for you graphic-card (I have a SIS 661/741/760)

I you are using kde (i do) then you should disable the enhanced logout-effect by adding the following lines to your $HOME/.kde/share/config/ksmserverrc

[Logout]
doUbuntuLogout=1
doFancyLogout=0

maybe this helps you too.

---

### Post by peterx14 on 2007-08-08
vga=791 worked perfectly for me -- thanks loads!!! :D

According to Device Manager, I have a SiS 65x/M650/740 graphics chip. It's got a native res. of 1024x768x24 so vga=791 suits me fine.

---

