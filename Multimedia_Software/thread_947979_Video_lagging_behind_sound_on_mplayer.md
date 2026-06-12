---
title: "Video lagging behind sound on mplayer"
date: 2008-10-14
forum: Multimedia Software
---

### Post by gully on 2008-10-14
Hi, I have a problem with mplayer on hardy.

Since I've upgraded my videocard (Nvidia 8800GTS 512mb), a new soundcard sound and video are often out of sync on the mplayer.
It starts out fine but after a while video starts to lag behind on sound, pausing for a second and then resuming the video syncs it up again, but it's still annoying.
I've already added the "framedrop=yes" line to mplayerconfig and I have the 169.something driver for my videocard, videos play fine on the totem player (but I prefer the mplayer.)

I have 2gb of PC6400 ram and a dual core cpu, so hardware isn't the problem.

Does anyone know of a way to fix this?

---

### Post by shirilover on 2008-10-15
Try -lavdopts fast:threads=2 as well.

---

### Post by gully on 2008-10-15
Do I have to add that to mplayerconfig? Because I tried and mplayer wouldn't open anymore...

---

### Post by shirilover on 2008-10-15
In that case, it would be:
lavdopts=fast:threads=2

Also, you could try
mc=0
or
demuxer=lavf

If any of them don't work, just disable them by placing a # in front of the lines.

---

### Post by gully on 2008-10-16
lavdopts=fast:threads=2 also disabled mplayer, but I found another thread that gave me a similar line that didn't disable mplayer but didn't fix the lag either, the other two lines didn't work either, but thanks anyway.

---

