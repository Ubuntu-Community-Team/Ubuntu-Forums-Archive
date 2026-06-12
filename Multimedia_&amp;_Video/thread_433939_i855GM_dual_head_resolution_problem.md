---
title: "i855GM dual head resolution problem"
date: 2007-05-05
forum: Multimedia &amp; Video
---

### Post by ozone on 2007-05-05
Hello all,

I have a Dell Latitude X300 laptop with Intel i855GM on-board video, using an up-to-date, fresh install of Ubuntu Feisty. I would like to use my Viewsonic VX715 17" TFT display together with the laptop's own video in a dual head configuration (with or without Xinerama).

The laptop display is 1024x768 while the monitor is capable of 1280x1024. I'm unable to make the external display use its native resolution when X.org is in dual head mode. The best I can get is either 1024x768 on both displays in dual head mode, or 1280x1024 on the external monitor with the laptop screen turned off. I do get proper resolutions in dual head mode in WinXP, so the hardware should be capable of this.

I have tried turning on and off different xorg.conf options such as UseFBDev and DDC. I don't know if it's relevant, but if I turn DDC on, the Viewsonic monitor goes "Out of Range" and refuses to display anything, so I keep it off and instead have specified proper(?) HorizSync and VertRefresh values in xorg.conf.

A relevant error in my Xorg.log seems to be this: 
(II) I810(1): Not using mode "1280x1024" (no mode of this name)

I have googled for this error message but the solutions I found to similar problems (e.g. setting VideoRAM or HorizSync and VertRefresh) did not help. X.org doesn't really tell what's wrong with the mode I'm asking it to use.

I have attached my xorg.conf, Xorg.0.log (gzipped due to attachment size restrictions) and lspci output.

I would be very grateful for any help!

---

### Post by kanogil on 2007-06-29
Hi Ozone,

I am experiencing the same difficulties as you. But could you tell me how you managed to get 1280x1024 on the external monitor with the laptop screen turned off?

Cheers :)

---

### Post by djgenesis on 2007-07-27
I am facing the same issue. 
On dual head, the first monitor is on 1024-768 and the other one remains locked at 640x480!! How can this be possible?!?!?!? 

My xorg.conf is SURELY correct:

```


Section "Monitor"
        Identifier "Fujitsu0"
        Option  "DPMS"
EndSection

Section "Monitor"
        Identifier "Fujitsu1"
        Option  "DPMS"
EndSection

Section "Device"
        Identifier      "ati0"
        Driver          "radeon"
        BusID           "PCI:1:0:0"
        Screen          0
EndSection

Section "Device"
        Identifier      "ati1"
        Driver          "radeon"
        BusID           "PCI:1:0:0"
        Screen          1
EndSection

Section "Screen"
        Identifier      "screen0"
        Device          "ati0"
        Monitor         "Fujitsu0"
        DefaultDepth    24
        SubSection "Display"
                Depth   24
                Modes   "1280x1024"
        EndSubSection
EndSection

Section "Screen"
        Identifier      "screen1"
        Device          "ati1"
        Monitor         "Fujitsu1"
        DefaultDepth    24
        SubSection "Display"
                Depth   24
                Modes   "1280x1024"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier "Multihead"
        Screen  "screen0"
        Screen  "screen1" LeftOf "screen0"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        Option          "Xinerama"
EndSection
```

How can this be?!?!

---

### Post by djgenesis on 2007-07-27
Found it!!!

> **Ziox said:**
> add these lines to both of your Monitor Sections:

[PHP]        HorizSync       30-65
        VertRefresh     50-75[/PHP]



I suppose we all have the same problem because we all use the same HowTo from [https://help.ubuntu.com/community/XineramaHowTo](https://help.ubuntu.com/community/XineramaHowTo)


I'll talk to this guy.

---

### Post by paterijk on 2008-04-24
Hi, 

I have the same problem with a Latitude X300 and an i810 graphic card. Could anyone who managed to solve this problem post his xorg.conf file? 

Thanx a lot, 

P.

---

