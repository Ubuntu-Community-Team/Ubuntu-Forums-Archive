---
title: "Fullscreen video hardware with scaling in MPlayer"
date: 2009-04-29
forum: Multimedia Software
---

### Post by markdavidoff on 2009-04-29
I'm trying to get MPlayer to play my videos Full Screen (cropping the sides) on my TV

Here is my command which does not work:

mplayer -fs -zoom -quiet -vo xv -monitoraspect 5:4 -vf scale=720:-3 <filename>

I assume the problem is hardware scaling with xv output, because I was able to get video to play on my server using the config below (but that was using software scaling with fbdev):

vo="fbdev"
fs=yes
zoom="1"
monitoraspect="4:3"
vf="scale=640:-3"

---

### Post by markdavidoff on 2009-04-30
Anyone got this to work?

---

