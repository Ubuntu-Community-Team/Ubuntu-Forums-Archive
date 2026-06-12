---
title: "NVIDIA/KDE 3.5.3 : enabling translucency-shadows effect -&gt; poor OpenGL performance"
date: 2006-06-05
forum: Multimedia &amp; Video
---

### Post by aurelieng on 2006-06-05
Hi all,

I'm currently trying the translucency/shadows effects that are available in KDE. I noticed that the framerate reported by glxgears is drastically decreased when these effects are turned on (1139.325 FPS instead of 16749.936 FPS).

My Dell laptop has a GeForce Go 6800 Ultra (rev a2, NV41.9), NVIDIA binary drivers 1.0.8762, with KDE 3.5.3. To recover the full performance, turning off separately shadows or translucency is not enough: I have to uncheck the "Use translucency/shadows" option above the opacity/shadows/effect tabs.
 
It's a pity that these nice effects cause such a performance drop ? Or maybe it is a bug ?

Cheers,

Aurélien

---

