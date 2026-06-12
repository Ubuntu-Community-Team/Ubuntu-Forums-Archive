---
title: "Nvidia dual monitor problem."
date: 2011-05-25
forum: Multimedia Software
---

### Post by FrigginGuy on 2011-05-25
So! I bought a cord from radio shack that allows me to plug two monitors to it and then run it into my computer. when i go to preferences-monitors only one is recognised as unknown. I have updated my invidia drivers and in the invidia gui it only recognizes one monitor as well and if i try to configure it to (twinview) the option is greyed out so that i cant even select it. I read that i may have to edit my xorg config to make this work which i have tried to no avail and my original config file looks as follows: 

Section "Device"
    Identifier    "Default Device"
    Option    "NoLogo"    "True"
EndSection

Shouldn't it say identifier invidia etc etc? Is it not recognising invidia? I have an invidia video card on my computer and i am running ubuntu 11.04

also both monitors work but show the same screen or mirror each other if that makes more sense but i cannot figure out how to make both monitors as one. 

Any help would be very much appreciated i have been struggling with this for quite some time. Many thanks to all!

---

### Post by wolfen69 on 2011-05-25
Start nvidia settings as superuser:
```
gksudo nvidia-settings
```
Post back what happens.

---

### Post by FrigginGuy on 2011-05-25
It brings up the NVIDIA X server settings but it only recognises the one monitor and twin mode is disabled

---

### Post by wolfen69 on 2011-05-25
What sizes are the monitors?

---

### Post by FrigginGuy on 2011-05-25
17 inch

---

### Post by wolfen69 on 2011-05-25
I was going to give you my xorg.conf file to try, but I use different sizes.

---

