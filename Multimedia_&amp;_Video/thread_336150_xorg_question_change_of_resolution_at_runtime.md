---
title: "xorg question: change of resolution at runtime?"
date: 2007-01-11
forum: Multimedia &amp; Video
---

### Post by wahlau on 2007-01-11
Hi all,

after all this time, i have always wondered what is the reason why we don't have easy/nice resolution change options like in the windows counterpart - you can also have the available resolution loaded, with or without the external display being connected to a notebook. I always change my xorg.conf files if i want to have some flexible change, which is not a problem if it stays at just xorg files change.. i must also restart my xorg in order to use the desired resolutions.

is it a xorg design issue when it come to such scenario? i cannot imagine how troublesome it might be, when i have 2 different LCDs in 2 places, and i have to get 3 different settings ready and restart if i swap from one to the other.

please tell me i am just ignorant, so that i can get the right resources to fix my problem above :)

thanks...

---

### Post by jpneron on 2007-01-11
Have you tried System/Preferences/Screen Resolution? That works for me without a restart or messing with the config files.

Jean

---

### Post by majoridiot on 2007-01-11
> **jpneron said:**
> Have you tried System/Preferences/Screen Resolution? That works for me without a restart or messing with the config files.

Jean

this will allow you to switch to any resolution defined in your xorg.conf.  if there are no other
resolutions available, check to see what is defined.  

```
gksudo gedit /etc/X11/xorg.conf
```

what you are looking for is something like this:

```
Section "Screen"
    Identifier     "Default Screen2"
    Device         "PCI"
    Monitor        "Generic Monitor2"
    DefaultDepth    24
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1024x768" "800x600" "640x480" **<-- resolutions for 16 bit color**
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "640x480" **<-- resolutions for 24 bit color**
    EndSubSection
EndSection

```

---

### Post by wahlau on 2007-01-12
perhaps i have not explained myself well :)

i have an external monitor in office serving me 1600x1200. so my xorg.conf has the configuration for 1600x1200 and 1280x1024 and 1024x768. Of course i will use the biggest possible. The question is about situations where i have booted the laptop with 1024x768, and wish to have 1600x1200 when i put the notebook on a docking station. however this will only give me 1024x768 at the external display, since while booting up, x server only detected 1024x768 and no higher resolution. This is the simplest fuss i would make since i must restart my gdm session in order to get 1600x1200 after connecting to the external monitor. 

the worst case is (which i hope to see in future) when i wish to switch freely between these modes, with or without external monitor/lcd attached, and able to select between xinerama, clone or single head *without* restarting gdm/xserver. This is so far not possible under linux, afaik. I can live with it, but seeing under windows is able to do that all the while, i felt a little... sour ;)

thanks for your answers anyway.. they are helpful and correct.

cheers,
wahlau

---

