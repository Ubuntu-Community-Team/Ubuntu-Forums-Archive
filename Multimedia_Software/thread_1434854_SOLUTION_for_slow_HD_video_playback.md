---
title: "SOLUTION for slow HD video playback"
date: 2010-03-20
forum: Multimedia Software
---

### Post by luther0 on 2010-03-20
Hey everyone! Greetings from Argentina.

I've been searching the forums up and down all afternoon, as well as two dozen other sites Google pointed me to, to try and solve my performance problem when playing HD video. I finally found a solution to it, and thought I'd share it.

**_My experience with the problem:_**

Like many others who experienced the same problem, my laptop has more than sufficient hardware power to play HD video files. However, and once again like many others, I had a most annoying performance problem (that is, overall jerkiness) that refused to dissapear no matter how many settings I tweaked, output engines I tried and video players I installed.

Since software didn't seem to be the problem, I turned my eye to hardware drivers and configuration, and struggled with that for the better part of another hour or two, to no avail.

**FINALLY**, I stumbled upon a most enlightening piece of information: the open-source codec Ubuntu uses is much slower than it's private counterparts at decompressing in real-time, which can slow the playback to a crawl in heavily compressed streams.

So I searched for a way to use a better codec, and found it.

**_THE SOLUTION:_**

Simple: emulate the CoreAVC codec for windows and plug it into MPlayer.

That might sound complicated, but just follow the instructions on the link below, 4 simple steps, and you're set.

[https://launchpad.net/~ripps818/+archive/coreavc](https://launchpad.net/~ripps818/+archive/coreavc)

Your only problem may be getting your hands on the CoreAVC codec. Google for it, I can't really address the issue here.

---

