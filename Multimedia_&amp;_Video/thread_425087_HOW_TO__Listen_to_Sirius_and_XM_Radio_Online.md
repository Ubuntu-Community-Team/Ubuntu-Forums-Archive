---
title: "HOW TO:  Listen to Sirius and XM Radio Online"
date: 2007-04-27
forum: Multimedia &amp; Video
---

### Post by birkhed on 2007-04-27
1) [http://ubuntuforums.org/showthread.php?t=413626](http://ubuntuforums.org/showthread.php?t=413626) 
2) [http://ubuntuforums.org/showthread.php?t=396738&highlight=restricted+formats](http://ubuntuforums.org/showthread.php?t=396738&highlight=restricted+formats)
3) Get the MediaPlayerConnectivity Plugin For Firefox
4) If you don't have it, get Amarok.
5) In Firefox goto Tools-->MediaPlayerConnectivity-->Configure
6) In the Real Media and Windows Media blocks change from:
       "/usr/bin/X11/totem" (or whatever media player you use) 
     TO:
       "/usr/bin/X11/amarok"
7)Start your respective radio service, and select a radio station.
8)Click the black box with the Media Icon, and Amarok should Start and the stream should begin.

NOTE: If you wish to watch Windows Media or Real Media video, change the MediaPlayerConnectivity's affinity 
             back to your player of choice.

Hope this helps, couldn't find any definitive information when I set this up.

---

### Post by amingus on 2007-05-04
Thanks!  I took your fix and loaded the totem-xine and XM comes in fine.:)

---

### Post by jangler on 2007-08-21
I found a Sirius Firefox extension that allows me to play Sirius through Firefox. In Firefox goto tools/add ons. Then go to "get extenions" and do a search for Sirius. I still get the infamous "missing plugin" error but it still works regardless.

---

### Post by pfeels on 2008-02-14
> **jangler said:**
> I found a Sirius Firefox extension that allows me to play Sirius through Firefox. In Firefox goto tools/add ons. Then go to "get extenions" and do a search for Sirius. I still get the infamous "missing plugin" error but it still works regardless.

I installed it but get no sound, I've read this is a common problem ...

---

### Post by Ftlgh on 2008-03-14
Couldn't get Amarok to work, but gxine does.  Thanks for the tip!

---

