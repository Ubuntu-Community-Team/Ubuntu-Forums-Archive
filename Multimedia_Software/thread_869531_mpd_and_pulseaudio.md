---
title: "mpd and pulseaudio"
date: 2008-07-24
forum: Multimedia Software
---

### Post by sistoviejo on 2008-07-24
mpd won't play any songs.
I get this message in /var/log/mpd/error.log:
```

Jul 24 23:35 : problems opening audio device while playing "the silos-holding on to life.mp3"

```
I tried the fixes in this wiki:
[http://mpd.wikia.com/wiki/PulseAudio](http://mpd.wikia.com/wiki/PulseAudio)
but no luck

---

### Post by sistoviejo on 2008-07-24
> **sistoviejo said:**
> mpd won't play any songs.
I get this message in /var/log/mpd/error.log:
```

Jul 24 23:35 : problems opening audio device while playing "the silos-holding on to life.mp3"

```
I tried the fixes in this wiki:
[http://mpd.wikia.com/wiki/PulseAudio](http://mpd.wikia.com/wiki/PulseAudio)
but no luck

Fixed!
You need to the fixes on the wiki.
I had to change /etc/mpd.conf and make mpd run as user root but I think that's an issue with my own computer. You probably don't have to do this though.

---

