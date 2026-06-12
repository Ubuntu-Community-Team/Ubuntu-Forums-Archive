---
title: "ATI Mach64 driver configuration"
date: 2009-05-11
forum: Multimedia Software
---

### Post by b@sh_n3rd on 2009-05-11
Hi I'm currently using a PC with an [COLOR=Green]ATI Technologies Inc 3D Rage Pro AGP 1X/2X[/COLOR] video adapter with 8MB video memory. I know that this question or similar questions may have been asked overtime but I came up with a solution to load the correct driver instead of the [COLOR=Green]vesa[/COLOR] driver that Ubuntu loads by default. I'm running Jaunty Jackelope BTW. 

I have a seperate PC with the famous troubling [COLOR=Green]i845[/COLOR] intel video adapter and that PC booted with vesa only too. Now I checked out, [http://wiki.ubuntu.com/X/Troubleshooting](http://wiki.ubuntu.com/X/Troubleshooting) and followed two separate links. From this I gathered that by editing the [COLOR=Green]xorg.conf[/COLOR] file, I'd be able to load the correct driver. I did this on the Intel PC and it worked, it loads the correct driver as it should even though there are a few probs with Jaunty.

Now back to ATI, I did the same thing on this PC with the ATI Rage Pro...here's my [COLOR=Green]xorg.conf[/COLOR] file:```
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "mach64"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection
```My Intel PC has "intel" following "Driver", which is what worked. When I run "[COLOR=Green]glxinfo | grep render[/COLOR]", I get:```
direct rendering: Yes
OpenGL renderer string: Software Rasterizer
```My Intel PC on the other hand detected the hardware and worked as it should even though it gave a small error message, which I will debug later on...Could anyone point out what I'm doing wrong on my ATI PC?

[COLOR=RoyalBlue](Note: Even though Intel and ATI Mach64 chips have their own problems on Ubuntu/Jaunty, I used it to compare so that the reader of this post would have an approximate understanding as to what I'm doing, wanna do and how)[/COLOR]

---

### Post by b@sh_n3rd on 2009-05-11
The way I see it, for some reason, the "mach64" driver isn't selected when X loads. Is there a way of forcing X to load the "mach64" driver? I've attached my current xorg.0.log file if that would help determine the problem...

---

### Post by b@sh_n3rd on 2009-05-20
No one knows about the mach64?? at least the xorg.conf!!?? :D...I thought I wouldn't get much replies on this...all i want is my comp to be fast...for that, I've gotta force X to load the correct driver...only thing needed here is the knowledge of xorg.conf coz I'm kinda new to it...

---

