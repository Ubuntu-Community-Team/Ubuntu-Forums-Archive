---
title: "Changing Display Driver (nvidia driver 180 issue)"
date: 2009-04-08
forum: Multimedia Software
---

### Post by pyrestrike on 2009-04-08
Hi all,

I just switched from the nvidia display driver 177 to 180 on my laptop, and it seems there is a compatibility issue. After I restarted post-install, my screen shuts off (not just go to black, but literally the screen doesn't display anything) after I log back in.

How do I go about changing the set display driver from 180 to 177? Is that even possible, or should I just do a simple reinstall? Thanks!

Brian

edit: I just now noticed that there is a different forum for hardware issues. If a mod would like to move/kill this one, I apologize :/

---

### Post by cariboo on 2009-04-08
I'm going to assume that you're running 8.10. Start in recovery mode and at the menu select xfix. Once it is done select resume and it should take you back to the desktop. Open synaptic and remove all mention of nvidia and restart X using Ctrl-Alt-Backspace. Now you should be able to reinstall the old driver.

Jim

---

### Post by pyrestrike on 2009-04-09
Ah, thanks!

I actually got it working by going into recovery mode and reinstalling the 177 package, after getting help.

---

