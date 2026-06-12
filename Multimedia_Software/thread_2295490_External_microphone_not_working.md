---
title: "External microphone not working"
date: 2015-09-19
forum: Multimedia Software
---

### Post by innominate2 on 2015-09-19
Hey guys,
I'm using Dell inspiron 5520, the built-in microphone is working (Y), but when I connect external microphone it does not show to work.
 upgraded to ubuntu 15.10, and still the same problem, in addition, gstreamer-properties didn't work giving an error "Failed to load UI file; please check your installation."
Screenshots for the alsamixer settings are attached
[ATTACH=CONFIG]264511[/ATTACH][ATTACH=CONFIG]264512[/ATTACH]

Thanks in advance

---

### Post by Bucky Ball on 2015-09-19
*Thread moved to **Multimedia Software**.*

Unless you are testing it, don't go to 15.10. Wrong way, go back. Not released until end of October and doesn't belong in this part of the forum. :)

I advise you install a supported release: 14.04 LTS supported until 2019, 15.04 until January 2016, then post back here if you're having the same problem.

If you want to stick with 15.10 and don't mind possible breakage and regular updates, I'll move this thread to the appropriate section for you. 

Try using Pulse Audio Volume Control and setting up your audio there. Plug the mic in, go to the Input tab and try the different devices in the drop down list next to 'Ports'. (Keep the volume slider fairly low for this as it may be loud when you choose the right device. You should see the level meter going up and down anyway when you use the mic with the right device.)

Good luck.

---

### Post by innominate2 on 2015-09-19
Thanks for reply, and sorry for posting in the inappropriate forum :D

I did as what you said and still having the same problem, tried another microphone and didn't work, tried it on another laptop and didn't work

---

