---
title: "mplayer and watching/recording tv"
date: 2005-11-19
forum: Multimedia &amp; Video
---

### Post by Blackie_Chan on 2005-11-19
I use tvtime to watch tv, but would like to use mplayer/mencoder to record tv shows.

Has anyone else been able to watch tv (or even better record tv with mplayer)? After making changes I get no audio, and the picture is really dark, making it difficult to see what's going on.

Here's an entry I added to my mplayer config:
```
tv=driver=v4l2:input=0:fps=29.97:normid=0:chanlist=us-cable:audiorate=32000:adevice=/dev/dsp1:amode=0:quality=75
```

---

### Post by oskude on 2005-11-22
just for the record, my miroPCTV doesnt work with v4l2. so, have you tried v4l ? (not v4l2)

---

### Post by Blackie_Chan on 2006-01-09
I can watch TV on mplayer now, but I get no audio. 

Here's my .mplayer/config:
```
tv=driver=v4l2:alsa=1:forceaudio=1:immediatemode=0:outfmt=yuy2:immediatemode=0:brightness=45:contrast=30:hue=46:saturation=50:norm=NTSC-M
```

Any suggestions on how to get audio while watching TV on mplayer?

---

