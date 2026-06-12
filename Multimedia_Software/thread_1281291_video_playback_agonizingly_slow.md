---
title: "video playback agonizingly slow"
date: 2009-10-03
forum: Multimedia Software
---

### Post by barna on 2009-10-03
I have installed 9.10-alpha, and now my videos (high-quality, large files) play back agonizingly slow. On the good old 7.10 (the last, where everything worked) they played without any problem.

My notebook is a Toshibas Satellite with 3.46 GHz processor, although somewhat tight on memory, but I don't think this is the reason: the output of free while running mplayer -vo x11 somefile.mp4 is the following:

```

             total       used       free     shared    buffers     cached
Mem:       1220668     604512     616156          0      27264     358204
-/+ buffers/cache:     219044    1001624
Swap:      1044216          0    1044216

```

Other players (kaffeine, vlc) also have the same problem.

I am somewhat tight on disk space, because I am very pessimistic about new releases, so I am experimenting with 9.10 on a small test partition before I erase 7.10. But I think this is also not the reason, I have 250 MB free on /:
/dev/sda6              4182436   3716804    253176  94% /


Any idea what can be the reason, and how to solve this?
Thanks

---

### Post by barna on 2009-10-05
Ok, this is most probably a driver issue, since I had speed problems with other apps as well:
[http://ubuntuforums.org/showthread.php?t=1278157](http://ubuntuforums.org/showthread.php?t=1278157)
So I am waiting for a next version of xserver-xorg-video-radeon

---

