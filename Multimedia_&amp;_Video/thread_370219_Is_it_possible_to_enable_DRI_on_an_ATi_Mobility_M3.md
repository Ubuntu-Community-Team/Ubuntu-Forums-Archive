---
title: "Is it possible to enable DRI on an ATi Mobility M3 ?"
date: 2007-02-25
forum: Multimedia &amp; Video
---

### Post by ikg74 on 2007-02-25
I recently began using ubuntu 6.10 (kernel 2.6.17.11-generic) and I'm trying to find what is necessary to enable DRI for the video card on the laptop is use.

The video card is the ATi Mobility M3 and at the moment rendering isn't enabled.

Any help and advice on how to do this correctly is gratefully appreciated.

Kind regards,

ikg74

---

### Post by ikg74 on 2007-02-26
I have attempted to enable DRI using the HowTo guide provided in this forum ([http://www.ubuntuforums.org/showthread.php?t=7200](http://www.ubuntuforums.org/showthread.php?t=7200)) but I'm still without direct rendering when I check glxinfo.

lspci shows me that the card is identified as:

01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility M3 AGP 2x (rev 02)

I'm not sure whether this card carries the mach64 chipset but I believe it does because I didn't get any errors when I installed the common and mach64 packages from: 

[http://dri.freedesktop.org/snapshots/](http://dri.freedesktop.org/snapshots/)

I selected common-20060403-linux.i386.tar.bz2 and mach64-20060403-linux.i386.tar.bz2

Before I installed those packages I also got the updated kernel, headers and compilation tools that the guide recommends.

I managed to find linux-686 and build-essential but I couldn't find linux-headers-686 for my kernel. My kernel version according to uname -r is 2.6.17-11-generic but when I try apt-get install linux-headers-2.6.17-11-686 I'm told the package could not be found. I did find a nonspecific linux-headers-686 package that didn't mention the kernel version and after I installed it I found that it is version 2.6.17-11 for my kernel when I checked with the synaptic package manager

The linux-headers that are currently installed are the following:

linux-headers-686                        version 2.6.17.11
linux-headers-2.6.17-10                version 2.6.17-11.34
linux-headers-2.6.17-10-generic     version 2.6.17-11.34
linux-headers-2.6.17-11                version 2.6.17-11.35
linux-headers-2.6.17-11-generic     version 2.6.17-11.35

The guide then says to reboot into the updated kernel if it wasn't installed already but I don't know how it's possible to reboot into the 686 kernel since I only have the option to boot into the 2.6.17.11-generic or 2.6.17.10-generic on the grub menu when I start the computer.

Does that mean that I have to compile the 686 kernel first ?

I did go on to install the common and mach64 DRI packages according to the subsequent instructions in the guide.

There were no problems with the installation of those packages and when I check lsmod it lists mach64 and drm

mach64      55680  0
drm           80536   1 mach64

However when I check glxinfo for the rendering status it shows me 

direct rendering: No

I had a look at the xorg.conf values as well but I don't know if anything needs to be adjusted. I'll add the relevant sections in case they have to be modified correctly

Section "Module"
           Load   "i2c"
           Load   "bitmap"
           Load   "dbe"
           Load   "ddc"
           Load   "dri"
           Load   "extmod"
           Load   "freetype"
           Load   "glx"
           Load   "int10"
           Load   "type1"
           Load   "vbe"
EndSection

Section "Device"
            Identifier   "ATI Technologies Inc. Rage Mobility M3 AGP 2x"
             Driver       "r128"   (this was set to "ati" originally)
             BusID       "PCI:1:0:0"
             VideoRam  8192     
             Option "NoAccel" "false"
(I added the last two items according to instructions from other users that have successfully enabled DRI)
EndSection

Section "Monitor"
           Identifier     "Generic Monitor"
           Option         "DPMS"
           HorizSync     28-70
           VertRefresh  43-60
EndSection

Section "Screen"
           Identifier      "Default Screen"
           Device          "ATI Technologies Inc. Rage Mobility M3 AGP 2x"
           Monitor          "Generic Monitor"
           Default Depth 16  (this was set to 24 but most users recommend 16 in order to enable DRI)
EndSection

Section "DRI"
           Mode   0066
EndSection

This final Extensions section was also added according to the suggestions of other users in this forum that got the DRI working

Section "Extensions"
           Option "Composite" "disable"
EndSection


If anyone has any further comments on something I have to correct in order to finally enable DRI properly I would be most grateful.

Many thanks to anyone who wishes to provided some help to allow me resolve this.

Regards,

ikg74

---

### Post by ikg74 on 2007-03-17
I managed to successfully enable DRI and 3D acceleration for this card and the drm and mach64 packages I tried to use previously are not necessary.

All that is needed is some editing of the xorg.conf file because it isn't possible to have direct rendering at a DefaultDepth hgher than 16 bit and 1024x768 resolution with this graphics card.

First of all it is necessary to set the DefaultDepth to 16 and then ensure that the resolution modes for Depth 16 are 1024x768 and below

eg.

SubSection "Display"
Depth 16
Modes "1024x768" "800x600" "768x576" "640x480" 

Secondly the following options should be entered in the section that corresponds to the video card driver

Option  "AgpMode"  "2"
Option  "EnablePageFlip"  "true"
Option "Accel" "true"

so that it looks like this:

Section "Device"
   Identifier     "Videocard1"
   VendorName  "ATI Technologies Inc"
   BoardName   "Rage Mobility M3 AGP 2x"
   Driver     "ati"
   BusID       "PCI:1:0:0"
   Option  "AgpMode"  "2"
   Option  "EnablePageFlip"  "true"
   Option "Accel" "true"
EndSection

Save the file, restart the X server and then check glxinfo

In this case the glxinfo | grep render command will produce:

direct rendering: Yes
OpenGL renderer string: Mesa DRI Rage 128 Mobility 20051027 AGP 2x x86/MMX/SSE

which matches with the lspci output for the VGA controller

---

