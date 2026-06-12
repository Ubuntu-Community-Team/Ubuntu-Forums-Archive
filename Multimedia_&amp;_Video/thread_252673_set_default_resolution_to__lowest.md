---
title: "set default resolution to  lowest?"
date: 2006-09-07
forum: Multimedia &amp; Video
---

### Post by kingmob on 2006-09-07
Is there any way i can change the default resolution that is picked from the xorg.conf? I have ubuntu with mythtv, connected to a TV, so i use 720x576. But i also use a VNC-server to access it and then a higher resolution is welcome. The video card supports TV-modes up to 1024x768, so that's what is set and it works fine. problem is i want the system to start in 720x576.
I use xfce as a window manager, but i'd rather solve it on the highest level, but i can't find it anywhere in the manpage or on the net how to set it in xorg.conf.

[edit] Seems i misinterpreted my problem. i figured that the first resolution i set would be used and that seems to be true. But a virtual screen size of 1024x768 is being used, creating 'panning' on my TV. The log looks like this:
```

(II) NVIDIA(0): Assigned Display Device: TV-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "720x576"
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0): Virtual screen size determined to be 1024 x 768
---
---
(II) NVIDIA(0): Setting mode "720x576"

```
And the problem is now that it must not set that virtual screen apparently (the TV-out can handle 1024x768 too, of this i'm sure).

---

