---
title: "NVidia drivers not loading"
date: 2008-04-06
forum: Multimedia &amp; Video
---

### Post by mlsquad on 2008-04-06
I am running Hardy Beta.  Back when it was still Alpha an update came in and killed the NVidia drivers.  Here's the info on my card:
lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)

What do I need to do to get it to use the packaged NVidia driver instead of vesa?

---

### Post by jacob01 on 2008-04-06
It sounds like im having a similar problem with gutsy, i still haven't found any thing to fix it. 

My problem is that i can install the driver, either using envy or the one from the nvidia site and then i can run startx from the command line and everything works good and thinks work great but when i shutdown then restart my comp i loose them and it forces me to low graphics and lets me pick the opensource driver. This wouldn't be a problem if i could get decent performance out of it (around 1fps in glxgears small)

lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GT (rev a1)

---

