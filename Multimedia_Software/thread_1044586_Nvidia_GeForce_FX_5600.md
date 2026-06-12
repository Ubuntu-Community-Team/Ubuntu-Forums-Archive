---
title: "Nvidia GeForce FX 5600"
date: 2009-01-19
forum: Multimedia Software
---

### Post by sammon on 2009-01-19
Hello,

I have Nvidia GeForce FX 5600 graphics card. I installed Xubuntu 8.10 (clean install) and activated proprietary driver for the card, ```
NVIDIA accelerated graphics driver (version 173) [Recommended]
``` Another choice in the list would be version 96.

The driver seems to be working: I can access different settings from Applications -> System -> NVIDIA X Server Settings and glxinfo command gives nice looking output, the glxinfo output is also attached here in glxinfo.tar package.

And now to the exact problem. I can play 3D games (like openarena, smokin guns, etc.) but when I have played some time, about 5-10 minutes, the wavy effect appears to the whole screen and lasts as long as I keep playing. It takes few seconds after I have quit the game and returned to the desktop to go away. And while playing after it starts the wavy effect it goes to black screen for little moments (lasts about a second) every now and then. Is the problem in the card, drivers, settings or where?

If it's any help for the matter, my kernel is 2.6.27-9-generic and my monitor Sony SDM-HS75. I have also included my xorg.conf file as an attachment. Command lspci | grep -i vga gives the output
```
01:00.0 VGA compatible controller: nVidia Corporation NV31 [GeForce FX 5600] (rev a1)
```

Thanks in advance.

---

