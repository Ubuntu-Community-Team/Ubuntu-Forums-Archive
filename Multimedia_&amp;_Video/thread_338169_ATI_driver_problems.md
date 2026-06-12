---
title: "ATI driver problems"
date: 2007-01-14
forum: Multimedia &amp; Video
---

### Post by Xenophoribic on 2007-01-14
Just recently intstalled Ubuntu, and I have a 9700Pro.  First time I installed, I got the drivers working perfectly fine, and unfortunately, had to format. Since then, I've had no luck in getting the drivers working again. I followed the unofficial guide on ubuntuguide.org and had no luck. fglrxinfo brings up the default:

display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)

Two formats now have netted no results. I'm at my wit's end. Any help is greatly appreciated.

EDIT: Fixed, thanks anyway

---

### Post by NT4usB on 2007-01-14
I tried them all too. Finally got them going on my 9600pro with [this]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")
Lots of posts on the subject [ here]("http://www.ubuntuforums.org/search.php?searchid=12744507")

---

### Post by Vord on 2007-01-14
Eh, I'm in the same room with him, and I just went try my hand at it. All that needed to be done was changing "ati" to "fglrx" in "device" in /etc/X11/xorg.conf. Problem solved.

---

