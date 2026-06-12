---
title: "h264 PC configuration"
date: 2009-01-15
forum: Multimedia Software
---

### Post by GuLRS on 2009-01-15
Hi!

I've been looking around (google) and couldn't find the answer! What kind of machine is capable of playing 1080p and 720p x264 files smoothly? I have a simple AMD Sempron64 2500 / 1GB RAM / Geforce 6200 256 MB RAM. Is my machine capable of playing those kind of files?

GuL

---

### Post by markbuntu on 2009-01-15
The quick answer is probably not. Since there is no h.264 gpu hardware support in any linux gpu driver yet you need powerful cpu to watch h.264 since the cpu must do all the decoding and rendering. That said, gpu hardware support is coming soon, probably within the year but your gpu must have built in support for hd. I don't know if yours does or not.

---

### Post by GuLRS on 2009-01-15
> Since there is no h.264 gpu hardware support in any linux gpu driver yet you need powerful cpu

How much powerful should be necessary?

GuL

---

### Post by tech0007 on 2009-01-15
This might be related to your inquiry:

[http://www.nvnews.net/vbulletin/showthread.php?t=123091](http://www.nvnews.net/vbulletin/showthread.php?t=123091)

It describes a gpu-accelerated decoding of h264 with a supported graphics card.

---

