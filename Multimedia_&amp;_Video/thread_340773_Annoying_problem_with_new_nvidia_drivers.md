---
title: "Annoying problem with new nvidia drivers"
date: 2007-01-17
forum: Multimedia &amp; Video
---

### Post by dangerous666 on 2007-01-17
Hello guys,

I have just installed the last nvidia driver which supports my card (geforce 4 Ti ), the 1.0-9631. Installation occurred sucessfully, but there is a annoying problem: everytime X starts, I get a poor refresh rate (43Hz), and I have to go to nvidia-settings and set the refresh rate to 85Hz. When X is restarted or the PC rebooted, the poor refresh rate comes back... I have no idea about how to solve this problem... I think my xorg.conf file is Ok, but.. anyway, it's atached to the message... 

I would really appreciate some help...

Ah, I'm running Kubuntu Edgy.

---

### Post by david_2001 on 2007-01-18
Wow, I must admit I had to find out how to get myself an xorg.conf like that :twisted:.

The only way that worked was running nvidia-xconfig without having an xorg.conf in place.  What I got was similar and seriously broken, though not quite as broken as yours!  If I were you, I'd delete my xorg.conf, start again from
```
dpkg-reconfigure xserver-xorg
```
and set it up nicely with the plain old "nv" driver before moving on to the nvidia driver.

Good luck!

---

