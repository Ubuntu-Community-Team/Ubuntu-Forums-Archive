---
title: "Tried several manuals, but cannot reinstall ATI driver. Help greatly appreciated."
date: 2009-10-28
forum: Multimedia Software
---

### Post by izg on 2009-10-28
I have an ATI Radeon HD 4650 graphics card and a few months ago when I installed Hardy Heron (8.04), simply downloaded the driver from the [ati website (here)]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.37&lang=English"), used the installation guide and all worked like charm.

After last week's after a kernel update (i think), things broke.  

So I've tried the following (after removing the fglrx drivers), etc:
1) used the installation guide in the link above unsuccessfully
2) followed both options in the following guide:
[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

I'm fairly new to linux, so any help will be greatly appreciated.  This problem is driving me nuts and I don't know what the policy is, but I'm willing to donate some cash via pay pay or whatnot (if allowed), at least enough for a glass of beer, to anyone who helps.

I'm running 3 kernels:
2.6.24-23-generic, 2.6.24-24-generic*, 2.6.24-25-generic

[SIZE=1]* This the version under which I managed to get the driver to work at one point, however I broke things as I naively "enabled" the driver under "hardware drivers."  I'd much rather get things to work under 2.6.24-23 as I have my wireless card working on this version (and this was a pain to install a few months ago--I fear I'll struggle again).[/SIZE]

After I do:

```
aticonfig --initial -f
```This is the xorg.conf file that gets generated and breaks things:

```
[SIZE=1]Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "InputDevice"
    Identifier  "Generic Keyboard"
    Driver      "kbd"
    Option        "XkbRules" "xorg"
    Option        "XkbModel" "pc105"
    Option        "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier  "Configured Mouse"
    Driver      "mouse"
    Option        "CorePointer"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    BusID       "PCI:7:0:0"
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    Monitor    "aticonfig-Monitor[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection[/SIZE]
EndSection
```

---

### Post by revanb on 2009-10-28
Hi

If you don't need 8.04 for anything specific, Why don't you try a newer version. 8.04 is quite old and Karmic Koala 9.10 is coming out tomorrow, 29 Oct 2009.

---

### Post by markbuntu on 2009-10-28
I have no problem with the newer fglrx drivers on Hardy. It is a very stable platform.

It is extremely important to remove old drivers before installing new ones or kernel updates will break, like what happened to you.

Since you enabled the driver from hardware manager you need to remove it. Use the Synaptic package manager and search and remove completely any fglrx packages or from the command line

sudo apt-get remove --purge xorg-driver-fglrx

To remove other fgrlx drivers and clean things up you should run

sudo sh /usr/share/ati/fglrx-uninstall.sh

Then you should reboot into the latest kernel recovery mode and use the fix x option and then continue. this should get you yup and running with the generic VESA driver.

When you get back to your desktop run the ati-installer script and

sudo aticonfig --initial -f

reboot and you should have a working fglrx, and no trouble with future kernel updates.

---

### Post by izg on 2009-11-01
markbuntu, thanks for your reply.  

I've tried those steps. But for some reason, that didn't work.  Since using ati's installer didn't work, I also tried generating packages. Now I'm concerned that trying out these different methods may have screwed things up.

I've been pretty busy and need a working linux box, but at some point I will try to reinstall.  For the afore mentioned reason, I want to avoid this step as it would take a while to recover all working applications--and I don't even want to try upgrading at this point.

Any other ideas will be appreciated. thanks.

---

### Post by mattyjk on 2010-04-12
> **markbuntu said:**
> 
To remove other fgrlx drivers and clean things up you should run

sudo sh /usr/share/ati/fglrx-uninstall.sh


Is this line important. 
Because when I run it I get this
> sh: Can't open /usr/share/ati/fglrx-uninstall.sh

---

