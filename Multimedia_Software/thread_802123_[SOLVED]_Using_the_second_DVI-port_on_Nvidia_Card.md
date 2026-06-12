---
title: "[SOLVED] Using the second DVI-port on Nvidia Card"
date: 2008-05-21
forum: Multimedia Software
---

### Post by WhizCas on 2008-05-21
I've been browsing for a while now on this problem and untill now I did not found a similar problem. At the moment I have a Nvidia 7950GT 512mb 8x AGP videocard with two DVI ports. The first DVI port is fysically broken and doesn't display the color red. No problem because I have the other port to connect the screen to you would say. But here is where the problem begins, Ubuntu only uses the first port as default. I've tried Nvidia's Twinview for a while with Clone on, but in certain situations this can cause errors. My current goal is to only use the second DVI-port for viewing the screen. Anyone has any idea where to start? Maybe an xorg.conf example? Thanks in advance...

---

### Post by aeiah on 2008-05-21
just go into the nvidia control panel (nvidia-settings) and turn off the display you dont want and hit apply. for me, if i want any lasting changes, i have to open with 

```
sudo nvidia-settings
```

but i always like to apply the settings without running it in sudo first in case i bork something, then re-do it with sudo for it to last. you should probably elect to save the changes to xorg.conf.

---

### Post by WhizCas on 2008-05-21
Thanks, that was easier than expected. It did the trick!:guitar:Rock on!

---

