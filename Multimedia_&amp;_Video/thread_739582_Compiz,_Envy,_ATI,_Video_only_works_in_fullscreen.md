---
title: "Compiz, Envy, ATI, Video only works in fullscreen"
date: 2008-03-29
forum: Multimedia &amp; Video
---

### Post by bthoward on 2008-03-29
Having trouble with video working in anything other than full screen.  Also if you turn off the unredirect fullscreen setting in compiz general settings that breaks fullscreen video too.

I just upgraded from 7.10 and used the latest Envy to install the latest ATI drivers.  In 7.10 I was still using the open source drivers. 

brett@lappy:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI MOBILITY RADEON X300
OpenGL version string: 2.1.7412 Release

Also while in full screen mode if you press a volume up/dn key when the volume level overlay pops up it blacks out all video output.  

If you use mplayer -vo x11 <file> it works in windowed mode but then when you full screen it won't scale.  

If you use XV you get full screen with good performance but you get no output when in windowed mode.

Reverting back to metacity makes things work but I'd like to get things working WITH visualizations.

I then also took a backup of my Xorg.conf and added the things mentioned at this link:
[http://blog.linuxoss.com/2007/11/22/update-running-compiz-fusion-using-ati-cards-and-aiglx/](http://blog.linuxoss.com/2007/11/22/update-running-compiz-fusion-using-ati-cards-and-aiglx/)

---

