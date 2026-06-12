---
title: "Audigy 2 sound not working"
date: 2009-01-28
forum: Multimedia Software
---

### Post by anti1029 on 2009-01-28
Hello!

I'm a new ubuntu user and I just installed 8.10 ubuntu. After getting setup, I proceeded to install updates. I remember my sound working right after install, but after installing updates it was lost.

Volume control at the top of my GUI is displayed and when I double click it, I receive the following message "No volume control GStreamer plugins and/or devices found."

I am not sure what else to try, I did a few searches and tried using the "sound problems" guide, but came up with no solutions.

---

### Post by timmil on 2009-01-28
Anti: Had the same problem with the same card as you. See the following post it fixed it for me.

- Tim

[http://ubuntuforums.org/showthread.php?t=1053058](http://ubuntuforums.org/showthread.php?t=1053058)

---

### Post by anti1029 on 2009-01-29
Timmil, 

Thanks for the response. I actually tried rebooting with the 2.6.27-9 kernel and I had the same problem. I'm not completely sure I booted into the kernel correctly though. I simply rebooted and chose the 2.6.27-9 ubuntu from the bootloader. Then I had to recompile my nvidia driver before I could startx.

---

### Post by mc4man on 2009-01-29
If your back in the -9 kernel and *sounds are working* you could just stay with that.
If you wanted to use the newer kernel (and didn't mind redoing your video yet again) the solution is further down in the thread. (#'s 9, 14

Actually if you were to turn the switch off in -9 as described in other thread, then when you booted into the newer one sound would be on. (function was inverted in the newer kernel

---

