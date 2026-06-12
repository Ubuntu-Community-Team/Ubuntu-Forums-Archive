---
title: "Xrandr Dual Head &amp; Screens?"
date: 2010-12-30
forum: Multimedia Software
---

### Post by complience on 2010-12-30
I am very confused with how Xrandr supports Dual screens.
It appears not to be supported according to this blogpost
[http://davelargo.blogspot.com/2010/01/xrandr-no-more-xinerama.html](http://davelargo.blogspot.com/2010/01/xrandr-no-more-xinerama.html)

I am attempting to setup Dual Screens on a Ubuntu 10.10 System with an ATI twin head card (DVI + HDMI)
Non-mirrored, separate desktops

However on connecting a device to the HDMI output - the DVI screen output appears to loose all panels, icons.
Only the mouse pointer & desktop background remains.

I believe the output is defaulting from screen 0 to screen 1.

I found a solution by creating two devices in xorg.conf and assigning one for each separate screen. BUT this created a new problem of loosing my mouse pointer.

Can anyone suggest how I can get my mouse pointer working or the correct way to setup dual screens.

advice from this post in apart (although not using Xinerama)
[http://ubuntuforums.org/showthread.php?p=1773624](http://ubuntuforums.org/showthread.php?p=1773624)

---

### Post by matt_symes on 2010-12-30
Hi

Have a read through this...

[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

Hopefully the section *how to setup a dual monitor* will help.

Kind regards

---

### Post by complience on 2010-12-30
The problem appears to be with Randr

When I connect the HDMI screen and run
xrandr -q

"can't open display"

---

### Post by matt_symes on 2010-12-30
Hi

> **complience said:**
> The problem appears to be with Randr

When I connect the HDMI screen and run
xrandr -q

"can't open display"

I have no experience using HDMI so i can't comment on that error message.

> I found a solution by creating two devices in xorg.conf and assigning  one for each separate screen. BUT this created a new problem of loosing  my mouse pointer.

Did you add an input device section to your xorg.conf file? That may fix the mouse issue.[FONT=monospace]

[/FONT]```
Section "InputDevice"
.....
EndSection
```

Kind regards

---

### Post by complience on 2010-12-30
I thought about the input devices option.

Was worried about tying them into into the Xserver would make them unavailable to anything else.

Strange that my bluetooth keyboard worked okay but the mouse did not.

Also i wasn't sure what to enter for my mouse (its also bluetooth)

---

### Post by matt_symes on 2010-12-31
Hi

> I thought about the input devices option.

Was worried about tying them into into the Xserver would make them unavailable to anything else.

Strange that my bluetooth keyboard worked okay but the mouse did not.

Also i wasn't sure what to enter for my mouse (its also bluetooth)

I'm not sure what you should be adding under the input section in xorg.conf either.

It is odd that it discovered you keyboard but not mouse.

Under System->Preferences->Bluetooth and you discover the mouse (can it see the mouse?). I don't have a bluetooth keyboard or mouse so i am not sure if they work in the same way as other devices. It might be worth looking though.

Kind regards

---

### Post by complience on 2010-12-31
I see the keyboard, don't see the mouse (but it works)

---

### Post by matt_symes on 2010-12-31
Hi

> I see the keyboard, don't see the mouse (but it works)

What? Both keyboard and mouse? Does this mean the problem is fixed?

Kind regards

---

### Post by complience on 2010-12-31
no.. obviously i reverted back to my normal xorg.conf once it became clear it killed my mouse.

the modified xorg.conf appears to kill input devices like mice but not bluetooth devices like my keyboard it seems.

---

### Post by matt_symes on 2010-12-31
Hi

Sorry mate. I don't have any experience with dual monitors with HDMI. Your setup is completely different to any i have worked on, so i must bow out (un)gracefully ;)

Good luck on getting it fixed and i wish you all the best for the new year.

Hopefully someone else here will have some ideas.

Kind regards

---

### Post by complience on 2010-12-31
Screen 0: minimum 320 x 200, current 2720 x 768, maximum 2720 x 1920
DFP1 connected 1360x768+0+0 (normal left inverted right x axis y axis) 1150mm x 650mm
   1360x768       60.0*+
   1280x768       59.9 +
   1920x1080      60.0     30.0     25.0     24.0  
   1776x1000      60.0     30.0     25.0     24.0  
   1680x1050      60.0  
   1400x1050      60.0  
   1280x1024      60.0  
   1440x900       59.9  
   1280x960       60.0  
   1280x800       60.0  
   1152x864       60.0  
   1280x720       61.0     60.0     50.0  
   1024x768       60.0  
   1152x648       60.0     50.0  
   800x600        60.3     61.0  
   720x576        50.0     25.0  
   720x480        61.0     59.9  
   640x480        60.0     61.0  
DFP2 connected 1360x768+1360+0 (normal left inverted right x axis y axis) 160mm x 90mm
   1360x768       60.0*+   24.0  
   1280x768       59.9 +   24.0  
   1920x1080      30.0     25.0     24.0  
   1776x1000      30.0     25.0     24.0  
   1680x1050      24.0  
   1400x1050      24.0  
   1280x1024      24.0  
   1440x900       24.0  
   1280x960       24.0  
   1280x800       60.0     24.0  
   1152x864       60.0     24.0  
   1280x720       60.0     50.0     24.0  
   1024x768       60.0     24.0  
   1152x648       60.0     50.0  
   800x600        60.3     50.0     24.0  
   720x576        50.0     25.0  
   720x480        59.9     50.0     24.0  
   640x480        60.0     50.0     24.0  
CRT1 disconnected (normal left inverted right x axis y axis)
CRT2 disconnected (normal left inverted right x axis y axis)
liminal@antec-ubuntu:~$

---

### Post by complience on 2010-12-31
Think im going to change the graphic card for a twin hdmi see if has any better luck.

but im not actually looking for specific hdmi help, I just want to know what I should enter in xorg.conf for a bluetooth mouse.

I've also notice this problem only happens if the screens are set to 'non-mirrored' if they are mirrors they are okay.

What config difference between the two in xorg is there?

---

