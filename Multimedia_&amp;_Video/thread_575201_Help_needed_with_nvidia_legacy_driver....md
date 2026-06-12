---
title: "Help needed with nvidia legacy driver..."
date: 2007-10-13
forum: Multimedia &amp; Video
---

### Post by epsilon72 on 2007-10-13
I have just installed xubuntu on an old Dell XPS T500, which uses a 16MB nvidia Riva TNT card (it calls itself 'diamond viper' though)

I'm having problems getting the nvidia-glx-legacy driver to work.

I've installed the 'nvidia-glx-legacy' driver as well as the nvidia-legacy-kernel-source package, but when I enable the driver by changing xorg.conf appropriately (nv--->nvidia), the x server is unable to start.

If I drop to the console with the modified xorg.conf and attempt to 'startx', it gives me the following, more or less:
```

Fatal IO error 104 on X erver ":0.0" after 0 requests (0 known processed) with 0 events remaining.

```
Booting up with the modified (nvidia-glx-legacy enabled) xorg.conf gives me some sort of xf86 error in the detailed x server (failure) output.

I usually use Gentoo, but that's on my new machine where I don't have to deal with old cards....does anyone know what I could do to fix this?

Thanks.

---

### Post by carlinuxlearner on 2007-10-14
Boot up in recovery mode, change your xorg.conf so it says "nvidia", then exicute "startx", post the the error here (the messages that starts with "EE").

C@RL

---

