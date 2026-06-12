---
title: "Fiesty Strange Vertical/Horizontal monitor frequency problem"
date: 2007-05-15
forum: Multimedia &amp; Video
---

### Post by wepage on 2007-05-15
I just installed Ubuntu Fiesty (1st time Linux user) and have a strange problem with the monitor frequencies. 

At boot up the monitor reports out of range ( H 35Khz, V 86.8 Khz).

It shows it's range as:   H 22-82 Khz     V 56-76 Khz

I have the refresh rate set to 70 Khz in Gnome

If I just wait for a while the monitor comes on and I can use it at full resolution (1280 X 1024).

This happens each time I boot, and also happens if I set my resolution to 1024 X 768 in Gnome

I would like to change the configuration so I don't have to wait through this each time.

Any suggestion ?  Thank You.

Hardware Details: 
Motherboard- Foxcon K7S41MG (Socket A) 
with SiS chipset and onboard graphics identified as "IntegratedUltra-AGP™IIGraphics"

Monitor:  Liquidvideo (Circuit City) 19" LCd

---

### Post by heimo on 2007-05-15
Editing VertRefresh and HorizSync lines in /etc/X11/xorg.conf to match your monitor specs may help.
[HOWTO: Solving resolution/refresh rate problems in Xorg]("http://www.ubuntuforums.org/showthread.php?t=83973")

---

### Post by wepage on 2007-05-15
Thanks for the input ,

But proper vertical and horizontal frequencies are already in xorg.conf.

The monitor just sees a vertical rate that is out of range.

I tried to auto generate a modline using a link in the howto reference. When i inserted that into
xorg.conf ubuntu would only boot to the command line - no graphical display.

Still unsure what to do next

---

### Post by heimo on 2007-05-15
Can you post your xorg.conf and its log file in a compressed attachment?

---

### Post by wepage on 2007-05-15
Here are files> I hope they are correct ones. Thank you for ta[ATTACH]32709[/ATTACH]king time with this.

---

### Post by heimo on 2007-05-15
Looks good to me. Backup your xorg (well - it's on these forums already, but you may want to have a local copy) and then you could try the following sections changed:
```
Section "Monitor"
    Identifier    "CMC 17 AD"
    Option        "DPMS"
    HorizSync    30-82
    VertRefresh    50-76 
    # V-freq: 75.00 Hz  // h-freq: 80.42 KHz
    Modeline "1280x1024_75hz" 151.83  1280 1360 1544 1888  1024 1024 1027 1072 
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter"
    Monitor        "CMC 17 AD"
    DefaultDepth    24
    SubSection "Display"
        Depth        24
        Modes        "1280x1024_75hz"
    EndSubSection
EndSection
```

---

### Post by wepage on 2007-05-16
I put in the suggested new sections into xorg.conf (replacing the original ones) and still get the same effect. The monitor screen reports out of range with a vertical frequency of 86.8Hz.

Then it pauses for a minute and  then comes on allowing me use Ubuntu.

Thanks for the help anyway.

---

### Post by heimo on 2007-05-16
It's a strange problem. There's possiblity that some option might help, but it takes experimenting. You can find some tips in the howto posted above.

---

