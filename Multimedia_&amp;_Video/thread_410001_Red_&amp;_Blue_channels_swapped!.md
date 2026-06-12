---
title: "Red &amp; Blue channels swapped!?"
date: 2007-04-15
forum: Multimedia &amp; Video
---

### Post by SubGothius on 2007-04-15
Just got Xubuntu 6.10 Edgy installed and running on PowerPC with an old ixMicro/IMS TwinTurbo 128+ video card ("imsttfb"), took me a while to realize why my colors appeared somewhat strange...  It appears that my Red and Blue channels have been swapped!  I.e., Red things are blue and vice-versa; hex value #00FF00 is correctly green, but #FF0000 produces blue, and #0000FF produces red! I know my monitor, cable, and vidcard are fine, as everything still displays fine when booted back in my other OS.  The only clues I've been able to find on this suggest it may be an Endian issue, perhaps a limitation/bug in fbdev (tho' my xorg.conf specifies the "imstt" driver), perhaps PPC-specific...?

Whaaa...  :confused: Anyone got a quick fix for this?

---

### Post by SubGothius on 2007-04-19
{Bump}
FWIW, this line of inquiry has been taken up in [another thread over here now](http://ubuntuforums.org/showthread.php?t=412142). ;)

---

