---
title: "HD Movie Playback"
date: 2008-08-24
forum: Multimedia Software
---

### Post by ferrarix on 2008-08-24
I'm currently using Ubuntu 8.04 (Hardy Heron) under WUBI and lately I got myself a couple of 720P HD movies encoded using Matroska Video Format (mkv). During playback, sometimes the image starts to lag a little bit or even hangs temporarily or gets out of synch from the audio.

My question is, can I make it playback using the VGA card as well? Just like the NVIDIA PureVideo Decoder available for Windows? I tried searching for it on the Internet but arrived nowhere.

_These are my current computer specifications:_
Intel Pentium 4 3.00GHz with Hyper-Threading (2 cores)
1GB DDR400 PC3200 RAM
Gainward NVIDIA GeForce 6200 card with NVIDIA drivers installed and updated.
160GB IDE/ATA 7200RPM HDD

The system is fully updated and the rest of my usage works with very good performance - better than Windows.

Thanks a lot,
ferrarix.

---

### Post by shirilover on 2008-08-24
MPEG-4 hardware acceleration is not available in linux.

I would use MPlayer with the following options:

-lavdopts threads=2:fast:skiploopfilter=all

---

### Post by ferrarix on 2008-08-25
When I type this in the terminal, MPlayer doesn't load, but instead gives me a list of switches I can use.

mplayer -lavdopts threads=2:fast:skiploopfilter=all

---

