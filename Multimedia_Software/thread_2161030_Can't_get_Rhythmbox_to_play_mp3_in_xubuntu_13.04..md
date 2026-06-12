---
title: "Can't get Rhythmbox to play mp3 in xubuntu 13.04."
date: 2013-07-09
forum: Multimedia Software
---

### Post by night-wing on 2013-07-09
Hi.

I desperately try to make rhythmbox play mp3 in xubuntu. I need rhythmbox and not gmusicbrowser (which indeed is a nice program) to get
access to my ipod classic in comfortable way.

I have all restricted extras, lame and all gstreamer plugins (good,bad,ugly,fluendo) installed. But I can't get it play mp3.
When I use the option to download needed plugins it starts searching ... und searches ... and searches... and never stop.

Something is missing... but what?

Regards
nightwing

---

### Post by mc4man on 2013-07-09
You can try this - 
Open home folder > .cache/gstreamer-1.0 & delete the <whatever>.bin file inside (different name depending on arch.
(- note .cache is a hidden folder

Or copy & paste this command into a terminal & run
```
rm ~/.cache/gstreamer-1.0/*.bin
```

---

### Post by night-wing on 2013-07-10
THanks. But this didn't work for me.

---

### Post by Yellow Pasque on 2013-07-10
Make sure you have these packages installed:
```
sudo apt-get install gstreamer1.0-plugins-ugly gstreamer1.0-plugins-bad gstreamer1.0-tools gst123
```
If you still can't play mp3's with rhythmbox, try gst123:
```
gst123 somefile.mp3
```

---

### Post by night-wing on 2013-07-18
Hey. 
All programs in xubuntu can play mp3 - vlc, gmusicbrowser...
But rhythmbox still refuses to do so :-(

---

### Post by azertyh on 2013-07-18
hello,
launch rhythmbox from terminal and play mp3 to see if there are error messages.

---

