---
title: "firefox and flash problems"
date: 2009-12-16
forum: Multimedia Software
---

### Post by vayu on 2009-12-16
I have Firefox 3.5 and 3.6 installed.  I also have Google Chrome. 
 
Flash 10 sound works in FF 3.6 but not video (if I hit refresh over and over sometimes video will work).  
FF 3.5 is the opposite. No sound, but no problem with video.

Flash in Google Chrome works fine for both sound and video.

If I use locate the only libflashplayer.so that shows up is in
/usr/lib/adobe-flashplugin/libflashplayer.so

If I right click on a flash object each of the three browsers show the version to be the same 10.1.  about:plugins also shows it installed and the same version.

I then went and copied a version 10.0 libflashplayer.so on top of the 10.1, then went to each browser with about:plugins all reporting 10.0 now.  Still no sound in FF 3.6 (video works better in 3.6 though)

Anyone have any ideas how to get sound working in FF 3.5?  (I'm on Kubuntu 9.10)

---

