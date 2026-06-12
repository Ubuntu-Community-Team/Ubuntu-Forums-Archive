---
title: "How to set maximum performance on Nvidia settings?"
date: 2012-01-14
forum: Multimedia Software
---

### Post by nibus on 2012-01-14
Hi there! I'd like to know for a long time how to set maximum performance on my Nvidia in startup.
I have ubuntu 11.10.
I  hope you can help me because i searched the response to this topic and i couldnt find anything at all.

Best regards!

---

### Post by wojox on 2012-01-14
Have you tried, in the terminal:
```
gksudo nvidia-settings
```

---

### Post by nibus on 2012-01-14
I know how to set it manually, but i want a way to set maximum performance automatically in startup, when i start the pc...

---

### Post by mc4man on 2012-01-14
You need to research the nvidia docu on their site if wishing something different than below.

The setting is made permanent thru an xorg.conf section - 
Here on this laptop I've set it to run at max perf. when on AC & use adaptive when on battery by creating an /ect/X11/xorg.conf file  & adding this section
(actually this is the only thing in my xorg.conf 

```
Section "Device"
  Identifier "NVIDIA GeForce"
  Driver     "nvidia"
  Option     "RegistryDwords" "PowerMizerEnable=0x1; PerfLevelSrc=0x3322; PowerMizerDefaultAC=0x1"
EndSection
```

The main reason here for this is that starting in 11.10 there is a noticable lag in compiz actions & some others like scrolling in FF. The upclocking doesn't happen quick enough

---

### Post by nibus on 2012-01-14
I've copied that code to my xorg.conf and saved.
Now i'm going to restart my computer, see if it worked or not.
Thanks!

---

### Post by nibus on 2012-01-14
It dindt worked... :(

---

### Post by mc4man on 2012-01-14
Then maybe you need to see what you can find find specific to your adapter on nvidia site or even try it's forum.
Can say it works as expected here - screens show 
screen 1  - on battery, after small wait drops to performance level 0
screen 2 - on Ac - is always on performance level 2

---

### Post by nibus on 2012-01-14
Didnt worked too... :/ I just want a way to set permanently nvidia graphics to maximum performance.

---

