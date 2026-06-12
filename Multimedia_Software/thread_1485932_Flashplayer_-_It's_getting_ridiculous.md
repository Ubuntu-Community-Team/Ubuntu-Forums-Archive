---
title: "Flashplayer - It's getting ridiculous"
date: 2010-05-17
forum: Multimedia Software
---

### Post by Swanmate on 2010-05-17
Hi everyone,

In early May I installed Ubuntu Lucid x64 on my PC. I've been using Ubuntu for 2 Years now (starting with 8.04), and besides being satisfied overall with the OS, there was always one thing that didn't work: Flash Videos. From poor performance to total crashes, it was never ever anywhere near good.

So, of course, the first thing I did in Lucid was downloading chromium, installing the Flash Plugin and try some streaming videos. And... surprise - It worked! Full Screen Flash Videos playing as smooth as it should be, no difference to Windows.

But, of course, that's too good to be true, and recently, after doing some upgrades via the Update Manager ('important' and 'recommended', new nVidia drivers as well I think), Fullscreen Videos were crappy all over again with the well known frame skips etc.

System:

AMD XII 245
GeForce 9800GT
4 GB RAM
Dual-Boot Ubuntu x64 / Win 7 x64

So - I wanted to ask, if there are any news on the "Flash-Front". Any new promising workarounds? Any chance Adobe... na, forget about that.

I think I've tried all the standard stuff concerning flash issues (trying the 64bit-version, which has even worse performance; cleaning up all flash versions to avoid any conflicts...).

So... any hints appreciated.

---

### Post by lovinglinux on 2010-05-17
See the [[COLOR="Sienna"]**Flash Optimization**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

But I wouldn't expect a miracle. Flash sucks. 

Perhaps you should try some of the options of the Flash Replacement section of my tutorial.

---

### Post by Swanmate on 2010-05-18
Thanks for the answer.

I remember putting

```

  Section "DRI"
  Mode 0666
  EndSection
  Section "Extensions"
  Option "Composite" "Enable"
  EndSection

```

into my xorg.conf in an erlier attempt to improve flash (in 9.04) but back then it didn't change anything, so I didn't expect much when I tried it again today. But hey, finally there is actually something that affects Flash performance at least *somehow*. Overall performance is better and smoother but there still are occasional annoying frame skips. 

Still a few steps away from Windows performance levels, but definitely an improvement and more on the watchable side now :).

---

### Post by lovinglinux on 2010-05-18
> **Swanmate said:**
> Thanks for the answer.

I remember putting

```

  Section "DRI"
  Mode 0666
  EndSection
  Section "Extensions"
  Option "Composite" "Enable"
  EndSection

```

into my xorg.conf in an erlier attempt to improve flash (in 9.04) but back then it didn't change anything, so I didn't expect much when I tried it again today. But hey, finally there is actually something that affects Flash performance at least *somehow*. Overall performance is better and smoother but there still are occasional annoying frame skips. 

Still a few steps away from Windows performance levels, but definitely an improvement and more on the watchable side now :).

I'm finishing the development of a Firefox extension that will provide a solution to lots of users with flash performance issues. I don't want to spoil the surprise, but I should have it ready in less than a week. I'm really excited with this new extension. Subscribe to my blog [RSS feed](http://lovinglinuxblog.blogspot.com/feeds/posts/default) or [Twitter](http://twitter.com/lovinglinuxblog) account to be notified about the release.

---

