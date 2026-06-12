---
title: "Refresh Rate Problem"
date: 2007-01-03
forum: Multimedia &amp; Video
---

### Post by skep on 2007-01-03
Hello!

I have a 21'' Nokia Multigraph 445Xpro monitor who supports a refresh rate of up to 114Hz @ 1280 x 1024. Right now I can only choose 85Hz in the System-Menue. So I've tried to edit to xorg.conf and changed the "1280x1024" part (in the default depth 24) to "1280x1024_95" (tried different values up to 114Hz), but then I do this, xorg jumps back to the second highest resolution ( 1024x768 ) at 85Hz. I also tried adding Option "UseEDID" "False" to the Device-Section, but this didn't help either. Is there any way I can force xorg to use something higher than 85Hz @ 1280x1024?
Could it be a problem with the nvidia drivers (I use the nvidia-glx-legacy driver) or my older graphic card (Riva TNT)?

UPDATE:
Solved the problem by adding "Modeline"-lines (generated with gtf) in the Monitor-Section in xorg.conf

---

