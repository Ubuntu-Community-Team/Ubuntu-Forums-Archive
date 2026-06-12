---
title: "Multiple Video card support in Ubuntu"
date: 2005-12-18
forum: Multimedia &amp; Video
---

### Post by wph on 2005-12-18
Hi,
 Was wondering if anyone out there knows how to build 2 video card types (and set up detection) into the ubuntu boot kernel and xorg.... I have a bootable usb drive that works fine with the NVidia Driver I have on my home machine, but the screen flickers during boot and then X fails - when I try to boot my Dell D810 laptop with an ATI Video Card......

Anyone have some advice?


TIA

WPH

---

### Post by poofyhairguy on 2005-12-19
[QUOTE=wph]Hi,
 Was wondering if anyone out there knows how to build 2 video card types (and set up detection) into the ubuntu boot kernel and xorg.... I have a bootable usb drive that works fine with the NVidia Driver I have on my home machine, but the screen flickers during boot and then X fails - when I try to boot my Dell D810 laptop with an ATI Video Card......

Anyone have some advice?


TIA

WPH[/QUOTE]

No. You have to change the driver each time for each. Use this command:

sudo dpkg-reconfigure xserver-xorg

---

### Post by afhp on 2005-12-19
Instead of reconfiguring X every time, there's something else you can do :
a) disable kdm/gdm ; the system will boot to a console prompt. The point is to start X manually.
b) edit /etc/X11/xorg.conf so that 
[INDENT]* it contains the appropriate "Device" and "Monitor" sections for your different setups
* it has a separate "ServerLayout" section for each of your setups ; each "ServerLayout" section will refer to the appropriate "Device" and "Monitor" section above
[/INDENT]
c) start X manually with the desired layout option :
```
startx -- -layout "layout-name-in-xorg"
```
(the double-quotes are not required)

You should end up with something along those lines :
```

# xorg.conf excerpts
Section "Device"
[INDENT]Identifier "nvidia"
# nvidia card configuration
[/INDENT]EndSection

Section "Device"
[INDENT]Identifier "ati"
# ati configuration
[/INDENT]EndSection

Section "Monitor"
[INDENT]Identifier "homeCRT"
# ...
[/INDENT]EndSection

Section "Monitor"
[INDENT]Identifier "laptopLCD"
# ...
[/INDENT]EndSection

Section "Screen"
[INDENT]Identifier "homeScreen"
Device "nvidia"
Monitor "homeCRT"
# ...
[/INDENT]EndSection

Section "Screen"
[INDENT]Identifier "laptopScreen"
Device "ati"
Monitor "laptopLCD"
# ...
[/INDENT]EndSection

Section "ServerLayout"
[INDENT]Identifier "home"
Screen "homeScreen"
# ...
[/INDENT]EndSection

Section "ServerLayout"
[INDENT]Identifier "laptop"
Screen "laptopScreen"
# ...
[/INDENT]EndSection

```

start XWindow with 
```

startx -- -layout home
or
startx -- -layout laptop

```

---

