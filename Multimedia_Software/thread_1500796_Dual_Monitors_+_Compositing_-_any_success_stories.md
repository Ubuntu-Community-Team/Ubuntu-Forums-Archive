---
title: "Dual Monitors + Compositing - any success stories?"
date: 2010-06-03
forum: Multimedia Software
---

### Post by mad_ady on 2010-06-03
Hello,

I've just upgraded to 10.04 and even if I am able to use my two displays with my Nvidia GPU, it bugs me that I can't use basic transparency controls on my desktop (compositing in Xfce). I've searched all over google and most links say it's impossible to mix Xinerama with Compositing, while others suggest using the old Xgl implementation will do the trick. 
I've also read things about Xrandr and that it might be a substitute for Xinerama, but it seems Nvidia drivers doesn't support it.

So, basically, I am at the end of my wits and I wanted to ask (shout?) if anyone managed to:
1. use two displays as part of the same desktop AND use compositing (window transparency)
2. or hack the compositing feature to work with some sort of software acceleration instead of hardware acceleration

Google lists all sorts of solutions, but none conclusive. So, is there a way out of this problem, maybe by using nouveau, or Xrandr, or something else entirely?

Thanks for listening...

---

### Post by gradinaruvasile on 2010-06-03
The compositing feature in Xfce (as in Metacity) is really slow - its software-based thus wastes lots of computing power for some fading effects. It is not the same as Compiz which uses real hardware acceleration and its really fast.
I couldnt even watch a movie (not HD mind you) withouth tearing and 100% CPU spikes on Core2Duo/Nvidia Quadro NVS 135M laptop while that Xfce compositing active.

Id say use Compiz if you want real display compositing - Xfce's own and Metacity's compositors are software based thus very ineffective (they are effective at slowing down everything graphical related).

PS: I used Compiz on dual monitors on a Nvidia Quadro NVS 280 and worked perfectly well.

---

### Post by mad_ady on 2010-06-04
Hmm, the strange thing is - I can enable compositing in Xfce and change all the transparency sliders I want, but I don't get any transparency effects if I have the second monitor enabled. With just one monitor, I seem to get hardware acceleration, because dragging windows over the screen like mad doesn't seem to affect the CPU...

Do you have any special nvidia configuration? Can you post your xorg.conf file so that I can test (with compiz)?

```

adrianp@frost:~$ cat /etc/X11/xorg.conf | grep -v "^#"


Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "1"
EndSection



Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "HP L1910"
    HorizSync       24.0 - 83.0
    VertRefresh     50.0 - 77.0
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "HP L1910"
    HorizSync       24.0 - 83.0
    VertRefresh     50.0 - 77.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "NoLogo" "True"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6200 LE"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6200 LE"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT-0: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "CRT-1: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

---

### Post by kid1000002000 on 2010-06-13
i have to reload with "compiz --replace" everytime i sync to two monitors... maybe that will solve your problem.  type it into alt+F2.

---

### Post by mad_ady on 2010-06-14
I've tried with compiz, and it seems I am closer to the truth - meaning I get these errors:

```

adrianp@frost:~$ compiz --replace
compiz (core) - Fatal: No composite extension

Launching fallback window manager
Xlib:  extension "RANDR" missing on display ":0.0".

** (xfwm4:8637): WARNING **: The display does not support the XRandr extension.

** (xfwm4:8637): WARNING **: The display does not support the XComposite extension.

** (xfwm4:8637): WARNING **: Compositing manager disabled.

** (xfwm4:8637): CRITICAL **: getBoolValue: assertion `G_VALUE_TYPE(rc[i].value) == G_TYPE_BOOLEAN' failed


```

My Xserver configuration is the default one (I'm running the nvidia driver), but I will look into enabling compositing for dual-screen under nvidia driver. And maybe I will try it with the nouveau driver (but I fear I will loose all acceleration...).

If you are using the nvidia driver and have a dual screen setup, can you please post your xorg.conf file (if it's not a minimal version)?

Thanks

---

### Post by mad_ady on 2010-06-14
I have tried to enable compositing in my xorg configuration by running 
```

 sudo nvidia-xconfig --composite 

```
... and although my Xorg.0.log says it is enabled, compiz and xfwm say it's not enabled:

```

adrianp@frost:~$ grep -i -A 1 "COMPOSITE" /var/log/Xorg.0.log
(**) Extension "Composite" is enabled
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
--
(II) Jun 14 08:37:18 NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) Jun 14 08:37:18 NVIDIA(0):     enabled.
--
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE

```

My xorg.conf ends with:
```

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

```

compiz --replace still says "The display does not support the XComposite extension.". 
Now, I'm not sure - is XComposite the same thing as COMPOSITE, or are they two completely different things?

---

### Post by tonymaro on 2010-06-16
Your problem is Xinerama.  Disable that in favor of Twinview and it should work.

---

### Post by Nandox7 on 2010-06-23
That's weird because I use a similar configuration.
A laptop connected to a external monitor or even when in the dock connected to two external monitors. The graphics card is an Nvidia Quadro NVS 140M so even older than that one.

My settings now is Nouveau driver + xfwm4 window manager and it works fine, I've enabled the xfwm4 compositor and I get transparencies a well as other support needed for AWN (the reason I need the compositor).  Only problem is some visual artifacts that show now and then but regarding performance I can't complain.

I'm using Nouveau because the Nvidia proprietary driver gives more performance but also gives a lot of headaches when I have to change display settings as Xrandr doesn't work.
Still Xinerama will give you a dual independent displays while probably what you want is twinview, to have both screens connected and not independent.

---

### Post by mad_ady on 2010-06-23
Thank you both for your replies. I haven't had time to try out the solution without Xinerama, but I hope I will test it later this week. 

From what I understood, Xinerama was a method to tell the window manager the layout of your screens, so that when you maximize a window, it will not fill both screens, but just the screen it's occupying. 

I have also played with nouveau on an older GeForce with Tv-Out, and it does support compositing (although it takes some performance penalty), but I haven't had time to test it further.

Nandox7: Xinerama doesn't give you independent displays (as in one X server for each screen), so I'm not sure exactly how it differs from TwinView, but I will give it a try.

---

### Post by supr0 on 2010-06-24
> **tonymaro said:**
> Your problem is Xinerama.  Disable that in favor of Twinview and it should work.

Really want to thank you for this simple yet effective solution!

Have always wanted dual monitor compiz and never figured that detail out!

Cheers :p

---

### Post by mad_ady on 2010-06-24
Yes, I finally had some time to tinker - and I can confirm - you can have transparency effects (compositing) with hardware acceleration and dual monitors with the nvidia drivers by using the twinview setup, without having Xinerama enabled. 
With this setup - Xinerama-aware applications still know the screens layout and only maximize on one screen instead of covering both screens.
There is one tip which might be useful - when changing configurations with Nvidia control panel, make sure that when saving the Xorg.conf file, you **don't** merge the settings - save the file from scratch and you'll have no problems.

Thanks again for your help. Now I am enjoying my desktop again :)

---

