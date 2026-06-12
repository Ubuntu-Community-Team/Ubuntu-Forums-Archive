---
title: "No picture in Movie Player (or any other)"
date: 2008-06-25
forum: Multimedia Software
---

### Post by ShakeyJake on 2008-06-25
Ive been watching movies in Movie player since I got the system, but suddenly I try today and get sound but a big, pixely mess in the video screen that doesn't even move.

I cant think of anything that Ive changed, the videos are just standard .avi that Ive watched before. This also happens in kaffeine and with all my video files.

I know this isnt much to go on but I just don't have any more info. 

Any ideas?

---

### Post by terry_gardener on 2008-06-25
you could try reinstalling the codecs/software, or another idea is to open the terminal and type: gstreamer-properties

goto the video tab and default output change it from autodetect to x window system (x11/xv) 

then retry. you might have to restart the x server but not sure.

---

### Post by Odrodzona-Sarmacja on 2008-06-26
If you did nothing, then maybe it is some segmentation fault. You need to uninstall your player, reboot computer and install it again. It should work then if it is segmentation fault.

---

### Post by ShakeyJake on 2008-06-26
Well it works fine after being rebooted now. 

If it ever goes awry again, Ill try these solutions.

Thanks guys.

---

### Post by aeiah on 2008-06-26
i had this problem once after checking out elisa. elisa uses gstreamer and perhaps you temporarily borked your video output by exiting a gstreamer application incorrectly or something. anyway, like you, my problem went away with a reboot.

---

