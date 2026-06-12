---
title: "mp3 support"
date: 2006-10-26
forum: Multimedia &amp; Video
---

### Post by gerowen on 2006-10-26
Rhythmbox, Xine, nothing will play sound in videos that use mpeg 2/3.  Xmms does, but it has its own mp3 package.  Right now I'm using VLC to watch videos, which isn't really a bad thing, but I'd like to have Rhythmbox able to play mp3's because I like to be able to manage my music library, podcasts, radio stations and everything all in one place.  I've put both the mplayer all and essential packages in /usr/lib/win32 and /usr/lib/codecs , and Xine picked up the video codec because now it will play videos in .avi format, just no sound.  When I used FC5 I just had to install the gstreamer-plugins-ugly package, but if I'm remembering right an update voided that tactic and I had to do something else, but I can't seem to remember what.  Help please?

---

### Post by pressman57 on 2006-10-26
Have you tried automatix? Worked for me.

---

### Post by gerowen on 2006-10-26
Sorry I'm an Ubuntu n00b, what exactly is automatix?  I can't find it in synaptic, :p.

---

### Post by ahsile on 2006-10-26
you don't really need automatix. if you:

```

sudo gedit /etc/apt/sources.list

```

And uncomment the universe repository you can then do the following:

```

sudo apt-get install gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly

```

(good may be installed already)

This should play all your music

---

### Post by gerowen on 2006-10-26
Thanks, that got the mp3 support working, still can't play xvid .avi movies in mplayer, but I've got VLC for that, thanks a ton for the help.

---

### Post by ahsile on 2006-10-26
do some searching on the forums for w32codecs. it should fix your video problems

---

### Post by gerowen on 2006-10-28
I finally got it all working, and didn't have to keep extra hard drive space for MPlayer.  I found Automatix, downloaded it, and it ROCKS hard core.  It made installing my multimedia codecs properly so Totem could see them as easy as two clicks.  No downloading extra software and having to know where to put it, easy as pie.  I just uninstalled MPlayer because Totem works with everything now, even the Mozilla plugin, and I didn't see any use in using up hard drive space with 3 or 4 different media players.  :biggrin: 

To make your life easier, [click here to download Automatix.](http://www.getautomatix.com/)

---

### Post by ahsile on 2006-10-28
Glad you got it working. I stay away from automatix because it uses it's own giant list of repositories rather than Ubuntu's.

---

