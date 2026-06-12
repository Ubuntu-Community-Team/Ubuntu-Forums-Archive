---
title: "ffmpeg DVD Poor Quality"
date: 2010-08-14
forum: Multimedia Software
---

### Post by Geffers on 2010-08-14
I recently downloaded a high quality bbc iplayer file (Madness in the Fast Lane), used the linux get_iplayer perl scripts file and the resulting file was an mp4

Excellent quality played on my Sony Bravia through the USB socket.

I wanted to put it on a DVD for more flexible TV playback so used ffmpeg -i myfile.mp4 -target DVD output.mpg (also tried vob) and the resulting file lacked video quality.

I thought -target DVD produced the best quality :(

Am I missing some settings.

Geffers

---

### Post by ron999 on 2010-08-14
Hi
I think that you need **-target pal-dvd** otherwise the default is ntsc.
It's pal for UK.

---

### Post by Geffers on 2010-08-15
> **ron999 said:**
> Hi
I think that you need **-target pal-dvd** otherwise the default is ntsc.
It's pal for UK.

Initially playing about with a 5 minute file of same quality I did try -target pal-dvd and ended up with what looked like a 4:3 rather than wide screen so ended up deleting it and trying other options.

Geffers

---

