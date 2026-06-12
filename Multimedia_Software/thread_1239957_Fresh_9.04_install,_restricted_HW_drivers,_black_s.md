---
title: "Fresh 9.04 install, restricted HW drivers, black screen. Where now?"
date: 2009-08-14
forum: Multimedia Software
---

### Post by hopwon on 2009-08-14
Hi
I am struggling with my new Sapphire 4350 HD graphics card. To take the idiot (me) out of the equation I've done a fresh install, run the updates and then activated the ATI/AMD drivers. Like before I get a black screen on boot but I can stll access the other ttys.
I'd appreciate some pointers as to where to go next to fix this problem.
Last night I did go through the manual install of thee drivers with the same results. 
Is there some settings in my xorg.conf file I'm missing perhaps? :
Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        DefaultDepth    24
EndSection

Section "Module"
        Load    "glx"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Driver  "fglrx"
EndSection

Thanks

---

### Post by Yellow Pasque on 2009-08-14
Duplicate thread: [http://ubuntuforums.org/showthread.php?t=1239029](http://ubuntuforums.org/showthread.php?t=1239029)

---

