---
title: "Dual Monitor Video Playback problem"
date: 2008-05-01
forum: Multimedia Software
---

### Post by Olrich on 2008-05-01
Hey all, I just installed Ubuntu 8.04 on my laptop, an Acer Aspire 5100, and got ATI drivers working just fine through Envyng.  I then tried to get dual monitors working, which was successful by following the guide here ([http://www.jumpingbean.co.za/blogs/mark/linux-ati-driver-tutorial-how-to](http://www.jumpingbean.co.za/blogs/mark/linux-ati-driver-tutorial-how-to)) and everything seemed to be working fine. 

However, whenever I tray to play a video on the external monitor, I get only audio, no video at all.  I've tried totem, vlc, and mplayer, and I experience the same problem.  All video plays fine on my laptop monitor, but will not play on the external one.

Has anyone else experienced this?  Does anyone have any solutions?  Thanks a lot in advance.

---

### Post by CarpKing on 2008-05-02
The Xv overlay can only be displayed on one monitor at a time.  You need to find a way to change which one.  With the open-source drivers I use gxvattr, but that probably doesn't work with the proprietary ones.  Dig through the options to see if there's one about "video overlay" or "Xv device."

---

