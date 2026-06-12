---
title: "Change DVD Region"
date: 2007-12-19
forum: Multimedia &amp; Video
---

### Post by ebs16 on 2007-12-19
Hi,

I recently purchased a legit NTSC DVD abroad that will not play on my American set-top DVD player (oops).  This is really annoying - I just want to watch the movie.  Is there a way to import and reburn the DVD with an American region?

Thanks!

---

### Post by timseal on 2007-12-19
Haven't tried it (yet) but this looks like what you're after: 
[http://dvd-create.sourceforge.net/](http://dvd-create.sourceforge.net/)

And next time you buy a dvd player, get one from [http://www.regionfreedvd.net](http://www.regionfreedvd.net)   I've bought two from them, both excellent.

---

### Post by ron999 on 2007-12-19
Hi

I expect that the DVD has a different region code number, not region 1, so your stand-alone dvd player won't play it.

If you copy the DVD and reburn it then the new one will be region 0 (which means that it has no region flag at all). Then it should play for you. 

For Ubuntu users the best (imo) application to use is k9copy, it's in the repository.

As well as copying the DVD, it has to be shrunk to fit onto a regular DVD+/-R disc. The software allows you to set the target size. (Mine is set at 4400MB).
8-)

---

### Post by ebs16 on 2007-12-21
hm... k9copy produced a dvd with the same region problem and i am running into issues compiling dvd-create.  any other ideas?

thanks for your help!

---

### Post by yabbies on 2007-12-21
NTSC is American
do you mean that it is a PAL DVD

If it is indeed NTSC running dvd decrypter in wine(I know, I know persecution) will rid the dvd of all region codes.

If it is PAL you will have to transcode the PAL ratio to NTSC ratio.

---

### Post by timseal on 2007-12-21
I think dvd-create is in the ubunto repository, but named dvdbackup.  give it a go, anyway.

---

### Post by jeffus_il on 2007-12-21
View the DVD on your computer, libdvdcss bypasses the region ...

---

