---
title: "XRandr Nvidia Twinview"
date: 2008-04-28
forum: Multimedia Software
---

### Post by Kiri on 2008-04-28
I'm trying to get a multi-monitor setup that I can swap on the fly between 3 displays (laptop, external LCD, TV)

So far I can use xrandr to swap between a single display (laptop or LCD) and twinview (laptop + LCD). This works fine. 

But I cannot seem to be able to get the TV to work. 
I want to be able to swap from 
Laptop + LCD
to
LCD + TV

I tried setting the metamodes in my xorg.conf, but could not seem to get it going. 


My current xorg is like this:
```
Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT: nvidia-auto-select +0+0, DFP: nvidia-auto-select +1920+400; CRT: NULL, DFP: nvidia-auto-select +0+0"
EndSection
```


Does anyone know how I can set this up?
Or has anyone got something like this working?

Note that I CAN get the setup working by replacing the xorg.conf with another one which is setup for TV + laptop display, but this requires restarting X. I want to get this working through xrandr, so I can do it on the fly..

thanks!

---

### Post by MrHippocampus on 2008-04-28
A wild stab in the dark would be changing the metamodes line to remove the identifiers in it so it applies to whatever two screens are currently available.

```
Option         "metamodes" "nvidia-auto-select,nvidia-auto-select; NULL,nvidia-auto-select;"
```

Other than that im not sure if what your doing can be done easily, have you had any luck using nvidia-settings?

---

### Post by Kiri on 2008-04-28
Using nvidia-settings I can set it up and save to the xorg.conf file and it will be how I want it after restarting X. But I have not had much luck getting the on the fly setup working from pressing Apply. It always seems to mess something up. 

I think for xrandr to work, I need to be able to enable and disable the different screens (since only 2 can be active at once).

---

