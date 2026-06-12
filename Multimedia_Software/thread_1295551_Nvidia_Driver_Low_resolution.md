---
title: "Nvidia Driver Low resolution"
date: 2009-10-19
forum: Multimedia Software
---

### Post by ilpiero on 2009-10-19
Hi all, after installing jaunty on my amd 3000+ machine to be used as a multimedia center i found that is impossible yo set a resolution higher than 800x600 (the monitor is a normal CRT that can handle 1280x1024 or higher i don't remember the model now but i will post it a soon as possible), and after activating the restricted nvidia driver the max res becomes 640x480.

I tried a puppylinux distro and a mandriva one (with nvidia driver) , both managed to set the 1024x768 resolution.

I googled a bit and found that this problem is pretty common.
I suppose is caused by Ubuntu not recognizing the monitor (the card is a geforce fx5700 anyway) and setting a low resolution to avoid to go out of frequency.


After reading some posts I tried to launch nvidia setting with sudo and adding lines like

```
SubSection "Display"
        Depth        24
        Modes        "1024x768"
    EndSubSection 
```

in my xorg.conf

nothing worked so far, any ideas?

thanks!!

---

