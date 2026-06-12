---
title: "No viewing of video files at all"
date: 2009-05-19
forum: Multimedia Software
---

### Post by oldrocker99 on 2009-05-19
I needed to do a reinstall. I followed, as I have before, the advice in this thread:

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

****NO**** video file (not .mpeg, nor .avi, nor .wmv) will play for me, in MPlayer, VLC, or exine. In every instance (except for MPlayer, which gives me sound only), the file starts to play, then the player exits.

Anyone have any ideas? This is a new one on me.

8.10 (still, thanks to ATI and the XOrg foundation)](*,)

:guitar:

---

### Post by xzero1 on 2009-05-20
For mplayer, try a different video driver. Use mplayer -vo help for a list of them. Use mplayer -vo drivername filename to play with the the selected driver.
Also try mplayer -v will increase the verbosity which might help.

---

