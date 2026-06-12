---
title: "Cannot play commercial DVDs"
date: 2009-01-25
forum: Multimedia Software
---

### Post by Category on 2009-01-25
I am having a major issue playing commercial DVD's with my DVD-RW drive. I have had no problem playing audio CD's, burning DVD's, or accessing data DVD's, but when I try and watch a commercial DVD movie, it just won't play - mplayer/totem/vlc all throw up I/O errors.

Here are a few lines from running dmesg, which seem to be the probelm -

```
[  398.474222] Buffer I/O error on device sr0, logical block 3993057
[  398.653758] end_request: I/O error, dev sr0, sector 15972228
[  398.848285] end_request: I/O error, dev sr0, sector 15972228

```

Many similar lines get repeated (hundreds of times), with varying sector numbers. 

I've installed w32codecs, libdvdcss2, libdvdread, etc after searching these forums, but nothing has helped at all.

Does anybody have any ideas what my problem is? I'm running 8.04, and my DVD drive is a Lite-ON IDE model.

---

