---
title: "Is there a bug in Totem in 7.10"
date: 2007-11-07
forum: Multimedia &amp; Video
---

### Post by irv on 2007-11-07
After upgrading to 7.10 and setting up codecs the Totem movie player worked on a couple of DVD I tested it on. Then this past Sunday I took it to church to play a DVD on and it gave me a message "Totem could not play "file://media/cdrom0/VIDEO_TS/VIDEO_TS.BUP, you are not allowed to open this file." So I went another route and used VLC media player and it plays just fine. I have a set of 4 DVD that will not play in Totem. If this is a bug I will report it, but I wanted to see if any one else is having this problem. Mind you, it is only these 4 DVD's I am can't play in Totem.

---

### Post by kamazu on 2007-11-30
It is the same for me here, any solutions?

thanks,

Manu

---

### Post by ElLute on 2008-02-21
same problem here. totem-xine is installed but totem doesn't play the dvd, xine is playing the dvd if called ```
xine dvd://

```
only opend by xine and then played, it is still scrambled.

mplayer and vlc just work fine (if opened dvd without menu).

dvdrip is working too.

is there written a bug-report or are there some solution-hints?

---

### Post by cor2y on 2008-02-21
In 7.10 totem-xine will play dvds, totem-gstreamer on the other hand is a toss up at least for me, just make sure the relevant dvd playback libraries (libdvdcss2, libdvdread, libdvdnav) are installed and use totem-xine.

---

### Post by wolfen69 on 2008-02-21
the only fix i have found is to remove totem and everything totem related. i think it's horrible.

then i install mplayer and vlc. life is good again.

---

