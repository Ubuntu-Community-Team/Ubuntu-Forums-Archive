---
title: "DVD playback is jerky"
date: 2005-11-22
forum: Multimedia &amp; Video
---

### Post by porsher_puddles on 2005-11-22
I have read through many threads but i still can't get the playback of my dvds to run smoothly, i have installed and tried xine,totem,mplayer but still a no goer,sound is fine everything else is ok, although i did notice visulisations in totem are also jerky.This is a p4 system by the way windows dvds run fine, i have installed all the codecs in the how to guide
any ideas on this one

---

### Post by darknuala on 2005-11-22
Try installing the totem-xine package.

---

### Post by pabc on 2005-11-22
is DMA enabled on your DVD drive?

Have a read here;

[http://www.ubuntuforums.org/showthread.php?t=30949](http://www.ubuntuforums.org/showthread.php?t=30949)

P

---

### Post by porsher_puddles on 2005-11-23
ok dma was set to on. And i edited my etc/modules,this is what it now looks like.
piix
ide-core
ide-cd
ide-disk
ide-generic
lp
mousedev
psmouse
nvidia

but i still have jerky dvd playback.
anymore ideas?

---

### Post by porsher_puddles on 2005-11-23
thanks for the advice it was indeed a dma problem, i obviously didn't do something right the first time i edited the file, it worked fine the second time around

---

