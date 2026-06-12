---
title: "[SOLVED] Audacity -- Exporting as an mp3 file"
date: 2007-12-16
forum: Multimedia &amp; Video
---

### Post by jake.mueller on 2007-12-16
I'm attempting to export a file as mp3 using audacity and when I try to do that a box appears which says:

"Audacity needs the file libmp3lame.so.0 to create MP3s. 

Location of libmp3lame.so.0:
/usr/lib/libmp3lame.so.0" and then i get the option to browse for the file and it's not there.

I then have the following option:

"To get a free copy of lame, click here -->" and when I try to down load it nothing happens.

Does anyone know how I can get this so that I might successfully export my file?

---

### Post by logos34 on 2007-12-16
try 

sudo apt-get install liblame0

---

### Post by jake.mueller on 2007-12-16
brilliant it worked!

---

### Post by logos34 on 2007-12-16
Glad to hear.  Enjoy audacity!

---

### Post by www.pragith.net on 2008-05-08
After using Ubuntu for a week or so, I feel that everything can be done with this small command >> sudo apt-get install NAMEofTHEtool

Nice!

Thanks

---

### Post by stevecoh1 on 2008-05-31
Thanks - a quick Google and this one is solved for me too.

Just asking, isn't there a bug in the packaging here somehow?  Shouldn't the apt-get for audacity (which I did a few hours ago) have picked up this dependency?

---

