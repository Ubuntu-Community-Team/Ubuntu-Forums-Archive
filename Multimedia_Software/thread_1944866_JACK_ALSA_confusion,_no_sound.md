---
title: "JACK ALSA confusion, no sound"
date: 2012-03-22
forum: Multimedia Software
---

### Post by kipjones on 2012-03-22
I just upgraded to JACK2, and now I have no sound output from system playback with any programs.  Frankly, I'm a little confused where ALSA ends and where JACK begins; when JACK is not running and I've quit Qjackctl, media plays fine through both soundcards listed in the terminal output below.

I'm kind of at my wits' end, any suggestions would be greatly appreciated.

Below is some output that pertains to ALSA, some verbose output from Qjackctl,
and a screenshot of my current configuration. When JACK is running, neither of the soundcards have output.

Thanks to anyone who replies.  I've been through many posts, but unfortunately am very confused.

Cheers!

---

### Post by kipjones on 2012-03-22
Jack is miraculously working, albeit with horrendous xuns.  Thanks to anyone who thought about replying!

---

### Post by Splooshie123 on 2012-03-23
Glad you got it working :) But Xruns are still a problem.

For xruns, keep increasing the Frames/Period setting until you get no more xruns. This will increase latency but its better than having choppy sound due to xruns.

---

### Post by kipjones on 2012-03-23
Thanks, Splooshie, but there's much more to it than that.  My hardware isn't terrible (3GB memory and 2x 2.3GhZ cpu) but my Jack latencies at best have been in the ~90ms range, still with occasional xruns.  

Today I tried out AVLinux's live CD and was able to get xrun-free performance with a latency of 23ms.  It's not nearly as elegant as Ubuntu 10.04, but it seems solid, and certainly dedicated to audio functionality.  I also intend to test drive DreamStudio and UbuntuStudio, whenever the 12.04 versions come out.

---

### Post by Splooshie123 on 2012-03-23
> **kipjones said:**
> Thanks, Splooshie, but there's much more to it than that.  My hardware isn't terrible (3GB memory and 2x 2.3GhZ cpu) but my Jack latencies at best have been in the ~90ms range, still with occasional xruns.

I know what you mean. The best performance I can get is ~42ms latency. Even then I still get the occasional xrun (although so far, it hasn't interfered with playback).

---

