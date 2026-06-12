---
title: "Intel GMA950: No proprietary Driver at Lucid?"
date: 2010-05-05
forum: Multimedia Software
---

### Post by juliank on 2010-05-05
Hey folks,

I'm still searching for a propiertary driver for my netbook (Asus EEE 901 with an Intel GMA950 graphic card).

lspci says:
>  Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03) 

Does someone know how to install a driver with 3D-support? Should I use a driver from [http://intellinuxgraphics.org/]("http://intellinuxgraphics.org/")?

I had no problems at Karmic, because the driver was found at "Hardware Drivers". Lucid doesn't show me any driver there.

Is there any correlation between the big intel-graphic issues and my 'problem'?

kind regards
 J.

---

### Post by xdevnull on 2010-05-05
I have an Acer Aspire 140 which uses the GMA950.  It works with 3D fine so far - at least I can run compiz with no problem.  I am having problems running an old game and the external monitor is not functioning at peak resolution, which it did with Karmic....so I'm trying to figure out what might be wrong.

---

### Post by okplayer02 on 2010-05-05
well if you open up synaptic and check and make sure you have the package xserver-video-intel installed this is the driver for your graphics card.

---

### Post by Yellow Pasque on 2010-05-05
Intel only has one driver for your GPU, and it's open-source. Are you having issues? If so, post output of:
```
LIBGL_DEBUG=verbose glxinfo
```

---

### Post by rdroberto on 2010-06-29
I'm having troubles with this video card, in a D945GTP motherboard (with lucid). The problem is the following: when the screensaver keeps runing for more than 10 mins, the system gives me "Ubuntu is running in low graphics mode" and I have to restart.

I'm posting the output of the command you suggested, and I'll post the other logs as soon as I get the error again

Thanks

$ LIBGL_DEBUG=verbose glxinfo

---

### Post by rdroberto on 2010-06-29
Here is the log

/var/log/Xorg.0.log

The error came this time one our after the screensaver started. Now I'm thinking the problem come when the screen (acer v173) goes to sleep, thus I'm disabling this feature.

---

