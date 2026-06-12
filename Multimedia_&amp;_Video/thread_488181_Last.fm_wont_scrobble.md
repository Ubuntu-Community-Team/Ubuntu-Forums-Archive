---
title: "Last.fm wont scrobble"
date: 2007-06-29
forum: Multimedia &amp; Video
---

### Post by infirmus on 2007-06-29
I downloaded and installed the deb file lastfm_1.3.0.58_i386.deb from the last.fm site and installed it, but I cant get it to detect what songs I'm playing in any music players.

I've tried Amarok, XMMS, and Rythmbox.

I also tried the old version of the lastfm from the Ubuntu repositories and same deal.

Is there some sort of setup that has to be done..? I know on Windows, the lastfm installer installs plugins for iTunes & foobar2000 etc..

---

### Post by infirmus on 2007-08-17
I found out that the lastfm package is only used for listening to streams.

Amarok has lastfm support built in.

---

### Post by drsaamah on 2007-08-23
YEAH!  Ive had the SAME problem.  WHEN I would stream with the last.fm player, it would show up but not when I played music in banshee.  And Banshee specifically supports last.fm scrobbling, so I shouldn't even have to have the last.fm player at all.  Anyone know what could possibly be preventing Banshee/EverythingElseLinux from scrobbling to last.fm?  Is there *anyone* using a linux media player that has been able to scrobble?

---

### Post by shen-an-doah on 2007-08-23
Last.fm doesn't work the same on Linux as on Windows, you don't need a seperate Last.fm programme. Amarok and Rhythmbox both have Last.fm support built-in, you don't need anything else.

For Rhythmbox it's Edit > Plugins > Last.fm > Configure and then just put in your username/password for Last.fm.

For Amarok: Settings > Configure Amarok > Last.fm

Other players I don't know, but usually if they don't have it built-in, you just have to download a plugin from their homepage.

---

### Post by drsaamah on 2007-08-26
Yeah that's what I was saying.  I have the last .fm radio even though i DONT need it, and banshee STILL doesn't scrobble.  Banshee also has the last.fm plugin standard like amarok.  Ive already set it up with my username and password but nothing shows up on my last.fm profile.  I guess I'll try amarok to see if it works, and maybe that'll will help me figure out why banshee doesn't work it.

---

### Post by MateuszP on 2007-08-26
I have this same problem. I configure Rhythmbox or Amarok, and scrobbling does't work. 
I see only: "Can't sending infp"

---

### Post by drsaamah on 2007-08-27
Not quite the same problem...
I tried amarok and it scrobbles just fine. Banshee still doesn't though.  I can't figure out what amarok is doing differently, and i really rather stick with banshee.  Amarok looks horrible in gnome, and i just like banshee's interface better. :-(

---

### Post by lupas on 2007-11-19
I have the same problem. Lastfm doesn't scrobble my music when i play with Ry. ANy solved suggestion ?

---

### Post by ato on 2007-11-20
[https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/163519](https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/163519)

---

### Post by exodunix on 2007-11-22
open banshee. go to Tools -> Audioscrobbler. the rest is self explanitory :)

---

### Post by lupas on 2007-11-23
> **exodunix said:**
> open banshee. go to Tools -> Audioscrobbler. the rest is self explanitory :)


Thanks for the reply . I recently noticed that the tracks are scobble after a while and not after each song .:lolflag:

---

### Post by Kingsfan on 2007-11-23
i just noticed that my rhythmbox stopped scrobbling about 120 songs ago...

---

