---
title: "Banshee not playing when firefox is running"
date: 2010-02-09
forum: Multimedia Software
---

### Post by yedidel on 2010-02-09
Running Kubuntu 9.10 64 bit.

If I start Firefox and then Banshee, Banshee won't play with a 
"GStreamer resource error: NotFound".

If I then close Firefox banshee will play, and then I can restart firefox and have sound in both, but that's very annoying.

Anyone has the solution?

---

### Post by boombox1387 on 2010-03-21
Does the error come up in a dialogue box?  Have you tried running Banshee from a terminal to collect more output?

```
banshee-1 --debug
```

I follow Banshee bugs pretty closely, and I haven't heard of this issue before, so it could be specific to KDE or the version of gstreamer you're using.  It could also be a Banshee problem.  If you report the issue on Launchpad, I'm sure someone will figure out which project is to blame.

---

### Post by yedidel on 2010-03-27
> **boombox1387 said:**
> Does the error come up in a dialogue box?  Have you tried running Banshee from a terminal to collect more output?

```
banshee-1 --debug
```

I follow Banshee bugs pretty closely, and I haven't heard of this issue before, so it could be specific to KDE or the version of gstreamer you're using.  It could also be a Banshee problem.  If you report the issue on Launchpad, I'm sure someone will figure out which project is to blame.

same error on debug output... doesn't give more details.

---

### Post by boombox1387 on 2010-03-29
From [this thread]("http://ubuntuforums.org/showthread.php?p=9044602") it looks like you're not the only person having this problem with the KDE + Firefox + Banshee combination.

I would highly recommend that someone experiencing this issue report a bug against the Ubuntu project in Launchpad: [https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu)

Someone there will help you determine which project is causing the problem, and they'll make sure that the bug gets reported to the developers of the correct project.  Since a little extra debugging might be necessary, it really would be best if someone experiencing the issue reports it.

---

