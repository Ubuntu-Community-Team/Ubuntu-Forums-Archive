---
title: "Problem playing .m4a files"
date: 2007-02-17
forum: Multimedia &amp; Video
---

### Post by foofightrs777 on 2007-02-17
I am currently having a problem playing .m4a files on my Edgy Eft installation. This problem however only exists in media library type programs such as Rhythmbox and Listen.  If I attempt to play the file through totem/vlc/realplayer or just about anything else it will play fine.  The error I receive in Rhythmbox is that the gstreamer plugin can not be found.

Is Rhythmbox looking for a version of the plugin which no longer exists?  I have enabled the universe and multiverse repos including some other common public repos.  Furthermore, I later attempted to fix this issue by instlling automatix's multimedia support. 

Would anyone have further troubleshooting suggestions?

EDIT:

I'm not sure if this is in anyway related but I also have problems with sound in flash9.  The video will play fine but all I get is silence.  I figured I should included this as well since its related to multimedia and audio.

---

### Post by foofightrs777 on 2007-02-18
Sorry, but I'm bumping this up.  Surely somebody must be familiar with gstreamer?

---

### Post by foofightrs777 on 2007-02-18
I have solved the problem.  Apparently a newer version of gstreamer was needed for some reason.  For my own reference and for anyone else who may have this issue the updated packages are here:  [http://ubuntu.cs.mtsu.edu/packages/multimedia/](http://ubuntu.cs.mtsu.edu/packages/multimedia/)

---

### Post by esaloch on 2007-02-22
It's not that you needed a newer version of gstreamer, you just needed the gstreamer-faad plugin that makes it able to play aac files

---

### Post by foofightrs777 on 2007-02-22
Ah I see.  Do you happen to know why this package isn't included?  Seems like it would make the migration to linux much easier for windows users. If suddenly half your music collection stopped working I'm sure switching would be made rather unappealing.

---

