---
title: "totem is not reading  mp3 files"
date: 2008-08-24
forum: Multimedia Software
---

### Post by bragaa on 2008-08-24
Hello,

I noticed that totem and some other readers cannot read mp3  files. However the alsaplayer is able to read the mp3 at least.
The same for the Helix Player, it is not able to read the rm files.

Are there any advise you may help me with?
Thanks

---

### Post by knattlhuber on 2008-08-24
ubuntu-freak's ["Comprehensive Multimedia & Video Howto"]("http://ubuntuforums.org/showthread.php?t=766683") is a very good thread that should solve most audio/video issues.

---

### Post by wolfen69 on 2008-08-24
what codecs have you installed? i just add the [Medibuntu]("https://help.ubuntu.com/community/Medibuntu") repos, and do ```
sudo apt-get purge totem-mozilla && sudo apt-get install mozilla-mplayer vlc
``` and i can play just about anything.

---

