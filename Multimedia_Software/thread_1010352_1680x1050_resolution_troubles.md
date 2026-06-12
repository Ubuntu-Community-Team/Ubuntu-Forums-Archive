---
title: "1680x1050 resolution troubles"
date: 2008-12-13
forum: Multimedia Software
---

### Post by Happypants on 2008-12-13
I just recently got a new monitor and its native resolution is 1680x1050 (Hannspree HF229H if you're curious :D ).  

The problem is whenever I add this resolution to my xorg (either through nvidia-config or nvidia-settings) and restart X the display shows up as just a thin line across the top of the screen.

I know that my video card supports this resolution (GeForce 6100:( ), so I know that's not the problem, but I can't figure out for the life of me what is though.

Any thoughts?

---

### Post by wolfen69 on 2008-12-13
your card is capable of 1680x1050. try: ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` then reboot or restart x.

---

### Post by albinootje on 2008-12-13
If you can't figure it out with dpkg-reconfigure, then look up the info of your monitor in the manual that came with it, and use one of the online Modeline generators to create a Modeline which you can then insert in the proper section in /etc/X11/xorg.conf

[http://xtiming.sourceforge.net/cgi-bin/xtiming.pl](http://xtiming.sourceforge.net/cgi-bin/xtiming.pl)

---

### Post by Happypants on 2008-12-13
Thanks for the reply.  That got rid of those pesky nvidia settings...  Heh... that was easy enough to fix, but I still have my issue.

I can use nvidia-settings to change the resolution, but upon restart of X it gets all wonky again (one thin line across the top of the screen).  Of course I could log in with low res, change it to the right setting, go about my business and change it back before every restart.  Personally though, I'm pretty sure I'll get tired of doing that after about the second or third time I have to fix my xorg cuz I forgot to adjust the resolution before shutting down X.:lolflag:

Here's my xorg.conf as it stands right now.  I have the 1024x768 setting in there from my old monitor.  It's working just fine, but the reason I bought a new monitor was to be able to stop using that one :p .

```
Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" 
    EndSubSection
EndSection
```

---

### Post by bwallum on 2008-12-13
Are you using Intrepid? If so do you have System>Administration>NVIDIA X Server Settings?

EDIT: Try editing modes to: Modes      "1024x768_60" The new monitor will be ok at 60Hz whereas your old monitor, particularly if it is a crt will probably be at a refresh rate higher than the lcd can handle.

I have had the same issue and have a number of ways that seem to work but try that first.```
gksudo gedit /etc/X11/xorg.conf
```

When you have your 22" up and running and have set it to 1680x1050 then use nvidia-settings to make it stick but beware, there is an issue with it. Follow LowSky's advice here [http://ubuntuforums.org/showthread.php?p=6300982#poststop](http://ubuntuforums.org/showthread.php?p=6300982#poststop)

---

### Post by Happypants on 2008-12-14
```
Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       30.0 - 110.0
    VertRefresh     50.0 - 150.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

It's surviving X restarts at 1680x1050 now.  I'm almost positive it was the sixth time I ran nvidia-xconfig that really did the trick...

Thank ya fellers

P.S. I'm 90(ish)% sure it wasn't just getting rid of that "mode" that did it.

---

