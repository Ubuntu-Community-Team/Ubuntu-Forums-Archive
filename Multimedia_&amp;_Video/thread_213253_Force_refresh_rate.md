---
title: "Force refresh rate?"
date: 2006-07-11
forum: Multimedia &amp; Video
---

### Post by grivad on 2006-07-11
So the refresh rate for my LCD is being set by default to 75Hz and it won't allow me to change it after installing the nVidia drivers (75Hz is the only option it shows).  The optimal refresh rate for my, or well any really, LCD is 60Hz.. is there a way to force 60Hz?  How?

TIA!

---

### Post by carontis on 2006-07-11
Well, I downloaded this program that permits to fix monitors and video cards. I send you the link hoping it will help you

[http://www.pcbypaul.com/software/GAMMApage.html](http://www.pcbypaul.com/software/GAMMApage.html)

bye

---

### Post by grivad on 2006-07-12
Thanks for the tip..

Is there another way to do this?  Via xorg.conf or otherwise?  A way to force the refresh rate system-wide?

---

### Post by Sykes2222 on 2006-07-13
I have the same problem. I tried forcing it to 60hz with a modeline in the monitor section but X wouldn't start (no screens found error).

Here is my monitor and device sections;

```

Section "Device"
        Identifier      "NVIDIA Corporation NV17 [GeForce4 MX 440]"
        Driver          "nvidia"
        BusID           "PCI:2:0:0"
        Option          "UseFBDev"              "true"
EndSection

Section "Monitor"
        Identifier      "L90D+ D-SUB"
        Option          "DPMS"
        HorizSync       31-80
        VertRefresh     56-75
EndSection

```

---

### Post by Sykes2222 on 2006-07-13
and as is always the way i found the answer 2 minutes later. This thread;

[http://www.ubuntuforums.org/showthread.php?t=199417](http://www.ubuntuforums.org/showthread.php?t=199417)

Shows the answer. Change your 1280x1024 mode to 1280x1024_60

---

