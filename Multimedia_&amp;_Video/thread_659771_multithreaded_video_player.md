---
title: "multithreaded video player"
date: 2008-01-06
forum: Multimedia &amp; Video
---

### Post by phillips321 on 2008-01-06
Hi guys,

just got me a 1920x1200 monitor, thus i want to try some 1080p movies on it.

The video is maxing out a single core on my cpu.

VLC = maxes out 1 core
mplayer = maxes out 1 core
totem = maxes out 1 core

are there any video players out there that can support two cores?

i have tried to use the "mplayer -lavdopts fast:threads=2" but get no joy. still only one core is being used.

PC specs:
D820 2.8GHZ DualCore
3GB Ram
7900 GS

I understand that my cpu is my limiting factor here but there must be some work around , i mean im pretty sure im not the only person who wants to watch movies in full hd but is limited due to the single threaded decoder?

---

### Post by kidders on 2008-01-07
Hi there,

Multithreaded decoding has nothing to do with the media player you use (well, *almost* nothing hehe) ... it's primarily decoder dependent. Firstly, the media you're playing has to have been encoded in a manner that can be processed by multiple threads in parallel (eg frame slicing). Then, you need to be using a decoder that supports multithreading ... many don't.

If you compile your media players yourself, you can get good control over what decoder libraries they're built against (and in turn, how the decoders themselves are built). If you're sure the media you're playing is multithreaded, it might be worth going down that route, or at least investigating where the bottleneck is ...[LIST]
[*]Media players that support multithreading will still only use one CPU unless the capability was enabled when they were built.
[*]Similarly, multithreading-enabled players won't take advantage of multiple CPUs if the decoder libraries they were built against weren't configured to do so, or simply can't do it.
[*]Some media players don't support multithreading at all, even if your decoder libraries do.
[*]And so on...[/LIST]

---

### Post by chuckman78 on 2008-06-18
Any hints on how to do this?

---

