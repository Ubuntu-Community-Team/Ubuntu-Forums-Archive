---
title: "deskto wider then screen when change resolution"
date: 2006-11-16
forum: Multimedia &amp; Video
---

### Post by Lukich on 2006-11-16
Hi. I'm trying to change the resolution of my screen to something greater then 1024 by 786.  There's a number of different methods listed on the forum, I tried to install the drivers from Nvidia site and through automatix.  Either way works fine, but the maximum res I get is still 1024x786.  Nvidia provides me with a list of other settings to change, such as digital vibrancy, hue, saturation, etc, but not resolution.  So I decided to add the desired resolution to xorg.conf, added 1280x800, restared xorg, and it worked, to an extent.  The size of the desktop is currently larger then the size of the screen so if I out my mouse close to the top, for instance, the destop would slide down and give me access to more desktop space on the screen.  I hope that makes sense.  What else do I need to do to keep the new resolution, but scale the desktop down to fit the size of the screen?
Thank you very much,
Luka

---

### Post by lixy on 2006-11-16
Are you using the Beta drivers?
Also, did you try [System> Preferences >Screen resolution] from the Gnome menu?

---

### Post by Lukich on 2006-11-16
The drivers I'm using came from Automatix, the driver is 1.0 - 7174.  Yes, I did try to go to Preferences>Screen Resolution, it still gives me the desktop that is larger then the screen.

---

### Post by Lukich on 2006-11-16
Actually, the situation has changed.  As I have rebooted the xorg one more time, my 1280x800 fits on the screen, but it now looks stretched vertically, as if the proportions have been broken.

---

### Post by Lukich on 2006-11-16
OK, I figured it out.  I used this installation instead of Automatix, [http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper), rebooted and then manually added the new resolution in xorg.  Ubuntu has the best support database I've seen in my life.  Thank you guys!

---

