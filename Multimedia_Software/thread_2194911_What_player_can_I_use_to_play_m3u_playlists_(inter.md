---
title: "What player can I use to play m3u playlists (internet radio)?"
date: 2013-12-21
forum: Multimedia Software
---

### Post by Nickolai_Leschov on 2013-12-21
I have several internet radio stations that offer their stremas as m3u files (playlists). What software can I use to play them? Having to install a player that is good for audio (aside from the other one, which I will use for video) is fine.

I have tried VLC and command-line mplayer, but they won't open my m3u's.

Here's an example m3u:
[ort.m3u]("http://idem-id.com/app/m3u/ort.m3u")

mplayer says:
> ```

Playing ./ort.m3u.
libavformat version 53.21.1 (external)
Mismatching header version 53.19.0



```

---

### Post by mc4man on 2013-12-21
Pretty much any player can play via a .m3u though the address's contained within have to be good which doesn't appear to be the case with your example.
(404 not found
for mplayer you need to use -playlist as in 
mplayer -playlist  /path/to/whatever.m3u

---

### Post by monkeybrain20122 on 2013-12-21
Yeah, it is a bad link. Downloaded the m3u file, can't play it with any player in Ubuntu. Got the same error message from vlc in Windows VM as well.

---

