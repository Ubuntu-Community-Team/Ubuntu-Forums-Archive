---
title: "DVD problems in Dapper with Matrox G400"
date: 2007-01-22
forum: Multimedia &amp; Video
---

### Post by arnethormodsen on 2007-01-22
I've just hacked together a system with an old ASUS CUV4X mobo.  I've got two video cards, and old ATI one and a slightly newer Matrox G400 (which I'm just running single-headed).  The G400 is the better card and I'd like to use it.

EVERYTHING works OK with the ATI card.  With the Matrox G400 I can't get any DVD player to work, including totem (Gstreamer and Xine), VLC, and a few others.  The symptoms are the same in all cases.  The DVD player opens it's screen then slilently dies.  Other than this the card to work fine, even plays AVI files.

I'm using the default stuff that Ubuntu builds into the X configuration (I actually reinstalled Ubuntu from scratch with the G400 card to make sure).  I tried updating the config with the framebuffer option (just for the heck of it) and this completely crashed X.

Any ideas would be helpful,

Thanks,

--arne

---

### Post by arnethormodsen on 2007-01-23
I know it's poor form to follow up to your own reply, but I found one answer after an hour or so in Google.  Disable "glx" in "xorg.conf.  Now I can play DVDs, but this just reeks of bad hack.  There must be a better answer.

--arne

P.S.  Also enabled AXP 4X while I was in there  (Option "AGPMode" "4"), didn't realize that this wasn't the default until I scrutinized Xorg.0.log.

---

