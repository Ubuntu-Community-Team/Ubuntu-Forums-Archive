---
title: "do linux nVidia drivers support hardware decoding of MPEG2/H264 ??"
date: 2007-11-24
forum: Multimedia &amp; Video
---

### Post by syxbit on 2007-11-24
check this site out
[http://www.driverheaven.net/reviews/8800GTs/hdplayback.php](http://www.driverheaven.net/reviews/8800GTs/hdplayback.php)
it shows the nVidia 8800GT dramatically decreases cpu usage during decoding of DVD/HDDVD/Blu-ray
is this enabled in the driver, and therefore only available in Windows?

---

### Post by syxbit on 2007-11-27
surely this is important to anyone with an nVidia!
anyone know?

---

### Post by barsanuphe on 2007-11-27
i've been trying to play 1080p videos, and my system struggles, even though i have an overclocked 8800GTS with an overclocked Q6600, even in opengl mode. i suspect something is wrong.

---

### Post by shirilover on 2007-11-28
MPEG-2 hardware acceleration is available using the nvidia drivers.
For mplayer, use -vo xvmc
For xine, use xxmc

However, H.264 hardware acceleraion is not available.

---

### Post by syxbit on 2007-11-28
how about in VLC ?

---

### Post by shirilover on 2007-11-28
The last time I searched for that, I found that the xvmc module in VLC was broken.
I don't know if it has been fixed since then.

---

