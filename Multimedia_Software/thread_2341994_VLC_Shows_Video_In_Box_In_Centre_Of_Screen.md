---
title: "VLC Shows Video In Box In Centre Of Screen"
date: 2016-11-02
forum: Multimedia Software
---

### Post by ThePowerpuffGirls on 2016-11-02
I tried taking a screenshot, but it won't show up.

The video shows up as the actual video size, and around it in black. What is even weirder is the if I have the menu drop-down, it goes behind the video, and is I minimise VLC, the video shows on the screen by itself, until I close VLC.

It is only on this computer. I've tried reinstalled Ubuntu, and as soon as I installed it, I installed VLC and played a video without changing anything and the same thing thing happened.

All of the computers are set up the same, software-wise, same software, etc.
This computer is the latest upgrade:
Motherboard: ASUS 150 Pro-Gaming/Aura
Graphics: Intel HD Graphics 530 Skylake
I'm using the integrated graphics.
RAM: HyperX 32GB (2x16GB) DDR4 2133MHz (Black).
Processor: Intel Core i7-6700K processor 4GHz (x8)

---

### Post by mc4man on 2016-11-02
Try opening vlc (no video, just open vlc - 
Tools > Preferences > Input/Codecs > Hardware-accelerated decoding > Set to Disabled
Also click on  Video > Output > choose OpenGL GLX ..
 Click Save, then try a vid.

(- If inclined to use Hardware-accelerated decoding then choose VA-API ... via X11

The gist is don't have either set to the default of Automatic as vlc is clueless with Intel gpu's particularly optimus machines

---

### Post by ThePowerpuffGirls on 2016-11-03
I'll try this later today and get back t you. Thank you. :)

---

### Post by ThePowerpuffGirls on 2016-11-03
> **mc4man said:**
> Try opening vlc (no video, just open vlc - 
Tools > Preferences > Input/Codecs > Hardware-accelerated decoding > Set to Disabled
Also click on  Video > Output > choose OpenGL GLX ..
 Click Save, then try a vid.

(- If inclined to use Hardware-accelerated decoding then choose VA-API ... via X11

The gist is don't have either set to the default of Automatic as vlc is clueless with Intel gpu's particularly optimus machines

It worked, thank you very much. :)

---

