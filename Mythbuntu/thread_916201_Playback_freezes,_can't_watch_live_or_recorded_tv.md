---
title: "Playback freezes, can't watch live or recorded tv"
date: 2008-09-10
forum: Mythbuntu
---

### Post by sbhargav21 on 2008-09-10
The TV display freezes up. When I record a channel it is recorded but playback freezes. I can use VLC player to play the recorded .mpg file & it plays well.
- Am fiddling with the playback settings but nothing has worked so far , CPU --, Slim

**My System:** Celeron 3.06 Ghz, 1 GB RAM, HVR 1600, ATI PRO 256 MB Card, TV Out

---

### Post by newlinux on 2008-09-10
go with CPU++ to start. The other ones like to try and use XvMC on some resolutions of playback (especially HD). You should look at your frontend logs to see what problems you are having when the playback freezes. That will give you your best information to troubleshoot this.

---

### Post by sbhargav21 on 2008-09-10
I tried the CPU++ & other setting . .still choppy ..

```
2008-09-10 18:21:28.424 TV: Changing from None to WatchingLiveTV
2008-09-10 18:21:28.450 Realtime priority would require SUID as root.
2008-09-10 18:21:28.523 Video timing method: USleep with busy wait
2008-09-10 18:21:31.129 WriteAudio: buffer underrun
2008-09-10 18:21:31.263 WriteAudio: buffer underrun
2008-09-10 18:21:31.340 WriteAudio: buffer underrun
```

That is the log of mythfrontend.
Thanks

---

