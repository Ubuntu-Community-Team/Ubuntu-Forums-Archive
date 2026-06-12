---
title: "Ubuntu 10.10 NVIDIA Problem"
date: 2011-01-20
forum: Multimedia Software
---

### Post by j.barker on 2011-01-20
I'm running Ubuntu 10.10 with an NVIDIA GeForce 6100 video adapter and my monitor seems to flicker whenever the the computer is processing. My system is up to date and I did install the recommended NVIDIA driver. The monitor isn't going blank or anything like that, it just seems like every once in a while different images will pop up for less than a second. Any ideas as to what the problem might be? I've attached a copy of the xorg.conf file as well:


Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection

---

### Post by murphycc on 2011-08-27
Were you ever able to fix the flickering? I have the exact same problem with Kubuntu 10.10, Geforce 6100. I used latest Nvidia driver but am now using v173 and the problem still occurs.

I tried changing vblank and such in the nvidia settings to no avail.

Makes me want to go back to the 2d Nouveau driver.

-Chris

---

