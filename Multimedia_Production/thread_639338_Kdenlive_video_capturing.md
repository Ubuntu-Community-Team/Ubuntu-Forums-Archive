---
title: "Kdenlive video capturing"
date: 2007-12-13
forum: Multimedia Production
---

### Post by amonsul on 2007-12-13
Hi!

Im trying to logging Videomaterial from my Panasonic camera. But in kdenlive im getting following erorr message:

> 
Too many output file names
Usage:
dvgra
[options] [file] [-
Try
dvgra
--help for more informatio
ALSA lib pcm_hw.c:1351:(_snd_pcm_hw_open) Invalid value for card
pipe:: I/O error occured
Usually that means that input file is truncated and/or corrupted.


Any help?
Thanks
Andres

---

### Post by theacoustician on 2007-12-13
It looks like Kdenlive depends on dvgrab to work.  There is a known bug with the current version of dvgrab (3.0) that's sitting in the repository in which piping doesn't work.  Until the repository is upgraded to dvgrab 3.1 or you install it from source, you probably won't be getting Kdenlive to work.

---

