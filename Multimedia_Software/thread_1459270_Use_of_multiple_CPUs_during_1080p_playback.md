---
title: "Use of multiple CPUs during 1080p playback"
date: 2010-04-21
forum: Multimedia Software
---

### Post by paopao on 2010-04-21
I have a high resolution file (1080p) encoded with H.264 and when I play it back, it lags at certain parts (and enough parts to destroy the job of watching the video).

I don't think that my computer is that crappy and it has been able to play many H.264 encoded files with high resolution - so there is always a possibility that this file is just encoded poorly (lacking a better computer, I cannot test).

For information, I'm running Ubuntu 9.10 64 bit.  I have a Intel Core2 Quad CPU Q9550 (@2.83 GHz).  I have 8 GB of RAM (forgot the speed off the top of my head).  And a Nvidia GeForce GTX 280 (1 GB of memory).

During the playback, the RAM is far from being completely used; however, it seems that one (and only one) of the cores of my CPU becomes saturated at 100% precisely at the moments in which the file lags.  When the CPU utilization is below 100%, there is smooth playback.

My question is - is it possible to use all four cores during playback, or is such a process not capable of easy parallel processing.

Another side question is, how can I be sure that my GPU is being used in the decoding process - or is that also being under-utilized?

Thank you.

---

### Post by cchhrriiss121212 on 2010-04-21
You can compile mplayer with multiple core support, but it's better to use vdpau output which enables the processing to be offloaded to your nvidia gpu. This guide is what I used:
[http://ubuntuforums.org/showthread.php?t=1037625](http://ubuntuforums.org/showthread.php?t=1037625)

---

