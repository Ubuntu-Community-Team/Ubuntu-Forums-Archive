---
title: "Nvidia dual monitor not working, not sure which driver"
date: 2014-05-15
forum: Multimedia Software
---

### Post by lile001 on 2014-05-15
[SIZE=3][COLOR=#333333][FONT=UbuntuRegular]I have struggled to get my displays working properly after a botched attempt to upgrade from 12.04 to 12.10.  Currently, I have one display working. Here is some information about what is installed. I don't really know how to proceed:
[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]System Tools displays only shows one monitor, called "Laptop". This is a desktop FWIW. I'd like to have both monitors back.
[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]nvidia-settings says I am not using the nvidia driver. It says to "run nvidia-settings as root and restart x-server", which I did. No change in symptoms. nvidia-settings does not look like it is supposed to - there is no x-server information on the left side panel, something is definitely not right here.
[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]I am apparently using "additional drivers" from Nvidia according to Software Sources in Ubuntu Software Center, and am using "the recommended driver" Nvidia binary Xorg from nvidia-current (proprietary, tested)
[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]$ xrandr -q
 xrandr: Failed to get size of gamma for output default 
Screen 0: minimum 320 x 400, current 1280 x 720, maximum 1280 x 720 default connected 1280x720+0+0 0mm x 0mm 1280x720 0.0* 800x600 0.0
640x480 60.0
640x400 0.0
320x400 0.0
[/FONT][/COLOR]

[COLOR=#333333][FONT=UbuntuRegular]$ lspci | grep -i nvidia
 02:00.0 VGA compatible controller: NVIDIA Corporation G98 [Quadro NVS 295] (rev a1)
[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Here is the "DEVICE" section of Xorg.conf which seems to have some relevance:[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Section "Device" 
Identifier "Device0"
Driver "nvidia" 
VendorName "NVIDIA Corporation" 
EndSection
[/FONT][/COLOR]

[COLOR=#333333][FONT=UbuntuRegular]I know just enough to know this stuff ain't right but not enough to fix it!
[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]What steps should I take to get my dual monitors back?[/FONT][/COLOR][/SIZE]

---

### Post by Alley_Oop on 2014-05-16
I just went through a similar problem and I had to switch back to the Nuveau driver for both monitors to be detected. It also improved my resolution.

I can't say if this will help you or not.

---

### Post by lile001 on 2014-05-16
Well, I just upgraded to 13.10, and suddenly the dual monitors worked again.  I don't know why.  I didn't change anything about monitors after upgrading, it just worked OK.  Nvidia-settings looks normal, twinview works.  I'm going to close the thread if there are no more responses in a bit.

---

