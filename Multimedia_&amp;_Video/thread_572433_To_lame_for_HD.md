---
title: "To lame for HD?"
date: 2007-10-10
forum: Multimedia &amp; Video
---

### Post by rhythminmind on 2007-10-10
So ive had a kubuntu media center setup for some time now for dvd & music. I have now stepped up in to the HD file playback world...
My system chokes on playback of HD files.
It can handle 720p but @ 1080 its choppy.
My media center is a couple of years old. Athlon 64 3400, gig of ram, 256 meg  video. It&#347; just a playback system. I would of thought it could cut it.. The files i want to play are 1080p  x.264 video with ac3 passed audio. 
Time for a new system? what are your thoughts?

---

### Post by bbg454 on 2007-10-10
I am having the same issue, i have an athalon 3200+, 1.5GB ram, 7600GT 256MB PCIe, reading from SATA drives. Used Envy to install latest NVIDIA drivers and am running the latest compiz Fusion (only cube enabled).

Haven't got the GLXGears numbers but its def accelerated.

any suggestions would be appreciated...

---

### Post by Heinz on 2007-10-21
You could try using mplayer with

```
-lavdopts skiploopfilter=all file.mkv
```

If you experience problems with that try "nonref" instead of "all".

Still too slow?

```
-lavdopts skipframe=nonref skiploopfilter=all
```

These options usually speed up H264 decoding. Don't know if your rigs can cope with the reduced data though.

---

