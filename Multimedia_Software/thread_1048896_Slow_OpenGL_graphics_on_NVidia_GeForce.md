---
title: "Slow OpenGL graphics on NVidia GeForce"
date: 2009-01-23
forum: Multimedia Software
---

### Post by jgb2185 on 2009-01-23
I just installed a new LCD monitor (Acer X223W), and have just enough knowledge to cobble together an xorg.conf file to enable the full 1680x1050 resolution. I am not smart enough to figure out why OpenGL graphics now are so slow. GL-based screensavers, and Second Life in particular, are so slow as to be unusable. I am running Ubuntu 8.04.

I was trying to enable both the full resolution and the Compiz advanced desktop effects. At some point in my struggles, I rebooted and found myself in a graphic setup screen, following a warning that Ubuntu was running in low-res mode. I had to pick a card, and I selected the Geforce 4. I am not certain this was the right choice.

I now have the full resolution and the Compiz effects, but very slow OpenGL-based graphics. Any help in sorting this out will be most welcome.

Details of the configuration can be found here:

[LIST]
[*][xorg.conf]("http://pastebin.com/f12859fd0")
[*][output of lshw]("http://pastebin.com/f2226ffd7")
[/LIST]
Thanks...

JGB

---

### Post by Melcar on 2009-01-24
Was performance higher before you switched resolutions?  Could be that your card is just too slow for certain things at 1680x1050 (games particularly get more demanding as the resolution increases).

---

### Post by jgb2185 on 2009-01-24
Honestly, I hadn't tried anything using OpenGL until after I had got the full resolution working. I can set the resolution lower and try it out.

I know that games can be demanding, but even the screensavers are running very slow. Solarwinds, for instance, is just a bunch of multicolored lines, but runs like molasses in January.

JGB

---

### Post by jgb2185 on 2009-01-24
It turns out that Melcar guessed correctly; the GeForce4 card cannot handle Second Life at the maximum screen resolution of 1680x1050. It runs SL okay at 1400x1050, and I can live with that for now.

Thanks...

JGB

---

