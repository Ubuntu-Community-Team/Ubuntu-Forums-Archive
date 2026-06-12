---
title: "Intel i915 video performance"
date: 2011-06-17
forum: Multimedia Software
---

### Post by dwazerik on 2011-06-17
Hi,

Like a lot of people I am having performance issues with the Intel video drivers, and this is driving me insane. I'm running Ubuntu 11.04.

A few months ago I bought a new notebook: A Thinkpad Edge 13. This notebook sports a "Intel Graphics Media Accelerator 4500MHD" graphics chip (source: [http://www.thinkwiki.org/wiki/Category:Edge_13%22](http://www.thinkwiki.org/wiki/Category:Edge_13%22)). I specifically bought a notebook with Intel chipset because my previous notebook had one and everything worked out of the box.

Now my main problem is that I cannot watch full-screen video. This is not application specific as I have tried different applications: VLC, Xine, S/Kmplayer, Totem. 
On my previous, old notebook I could watch up to 1080p video without any performance loss, in full screen. On my new notebook, this is not possible. Video gets choppy and I get audio delays.

Now I am not a complete Linux noob, I'm a part time admin. I've tried different thinks: enabling KMS (this gave a small performance boost), playing around with different settings in xorg.conf and I'm using the xorg-edgers ppa for the latest bleeding edge Intel drivers. YET, I still can't enjoy a movie on my notebook.

I hope somebody can give me any hints as what to try next, I'm ready to throw this notebook out of my window (or start running Windows).

Here's my xorg.conf during the best performance I can get:
```

Section "Device"
     Identifier      "Configured Video Device"
     Driver          "intel"
     Option "Shadow"     "True"
     Option "AccelMethod" "uxa"
#    Option "EXAOptimizeMigration" "true"
#    Option "DRI"       "False"

EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection
```

---

### Post by dwazerik on 2011-06-22
Friendly bumb

---

