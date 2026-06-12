---
title: "videos blank with second screen"
date: 2010-08-25
forum: Multimedia Software
---

### Post by neiljansons on 2010-08-25
Hi there
Video files (eg. .mpg, .avi, .flv) work fine on my Dell Inspiron 6400 laptop until I plug a second monitor (or data projector) in.
Once the second screen is plugged in the sound plays but the videos are blacked out.
It was a bit embarrassing when I went to do a presentation today.
Running Ubuntu 10.04
Thanks
Neil

---

### Post by neiljansons on 2010-08-27
I did another test.
If I change the monitor settings to duplicate the desktop rather than extend it (tick the box that says "Same image on all monitors") then they work correctly.
But if that box is not ticked then the video is black but the sound plays.

---

### Post by Plippo on 2010-09-06
Have you tried moving the window with the video on the other screen? Some graphics cards can only display video on one screen. This also happened on Windows for me with an ATI card.

---

### Post by neiljansons on 2010-09-06
> **Plippo said:**
> Have you tried moving the window with the video on the other screen? Some graphics cards can only display video on one screen. This also happened on Windows for me with an ATI card.

No it doesn't matter which screen I run the video on. It is black on either.

BTW the computer is a Dell Inspiron 6400. I often have a 19" LCD monitor plugged into the VGA port or sometimes a data projector. The result is the same.

---

### Post by neiljansons on 2010-09-20
I guess I must be the only one with this problem.

If I go to the Monitor Preferences, select the second monitor and then click on off, the video clips will run on the first screen.
If I turn the second screen back on they go black / blank again.
(basically the same as removing the second screen but easier and quicker to do)

---

### Post by neiljansons on 2010-09-20
Just doing some searching and found this - [http://ubuntuforums.org/showpost.php?p=9774192&postcount=9]("http://ubuntuforums.org/showpost.php?p=9774192&postcount=9")
> You may have set "ximagesink" ("X Window System (No Xv)") as video-output.
This means, that your cpu is doing all the work. Change it to "xvimagesink"
("X Window System (X11/XShm/Xv)") in order to let your graphics card do the work.

Mine was already at "xvimagesink" but when I changed it to "ximagesink" (which was NOT recommended) - now it works.

What is happening here?

---

### Post by jessiehilty on 2010-09-20
Just download vlc. It's much better than the average media player since it plays virtually any video/audio file format out there and has already all the codecs preinstalled. There are lots of other near features too. If you don't know where to look then check out the vlc player download page.

---

### Post by neiljansons on 2010-09-20
> **jessiehilty said:**
> Just download vlc. It's much better than the average media player since it plays virtually any video/audio file format out there and has already all the codecs preinstalled. There are lots of other near features too. If you don't know where to look then check out the vlc player download page.

VLC is not the panacea you think it is.
Changing the video output plugin to "X Window System (No Xv)" allows me to view video with any player EXCEPT vlc.
VLC displays a black screen either way.

---

