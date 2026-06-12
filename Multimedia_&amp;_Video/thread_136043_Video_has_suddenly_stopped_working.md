---
title: "Video has suddenly stopped working"
date: 2006-02-25
forum: Multimedia &amp; Video
---

### Post by dgrafix on 2006-02-25
Hi,

Im wondering about my video setup, it was working fine for ages with an nvidia gf4mx then last night, it decided to reboot with 640x480 with 256color @60htz. I have checked the options in gnome and thats the only option i have. xorg.conf has also been checked and i notice the default color depth and resolution is all correct.

Whats going on!!! :(

I did notice however that in xorg.conf the monitor is specified wrong, (i bought  new one a few weeks ago) although i dont think this is related as its been working fine for weeks. (although i cannot remember if i have rebooted or not since plugging it in!)
If this is the problem, how do i autodetect hardware (like the add new hardware function in windows). Or do i simply write "plug and play" in the monitor section?

---

### Post by bluevoodoo1 on 2006-02-25
[QUOTE=dgrafix]If this is the problem, how do i autodetect hardware (like the add new hardware function in windows). Or do i simply write "plug and play" in the monitor section?[/QUOTE]

```

sudo dpkg-reconfigure xserver-xorg

```

---

