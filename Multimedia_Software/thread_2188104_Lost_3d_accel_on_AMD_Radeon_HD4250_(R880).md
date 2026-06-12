---
title: "Lost 3d accel on AMD Radeon HD4250 (R880)"
date: 2013-11-15
forum: Multimedia Software
---

### Post by bigbrownepaul2 on 2013-11-15
I have been using my Acer Aspire 7540 with Ubuntu since 8.04 but this week my card AMD Radeon HD4250 (R880) lost its acceleration and my desktop has slowed to a crawl.

I am using the open source driver ( never bothered with catalyst), I have followed all the diagnostic threads found here previously with no luck.

Anybody have any pointers, its not in a blacklist I can see the only issue I can report is on boot there is a warning message about failing to load amd.bin microcode.

[http://paste.ubuntu.com/6422146/](http://paste.ubuntu.com/6422146/)

Tried all I know and been unable to get back my 3d accel.

Help is most appreciated, but its probably something stupid on my part.

---

### Post by Yellow Pasque on 2013-11-15
```
[   17.372543] r600_cp: Failed to load firmware "radeon/RS780_pfp.bin"
[   17.372555] [drm:r600_startup] *ERROR* Failed to load firmware!
[   17.372561] radeon 0000:01:05.0: disabling GPU acceleration
```

Try reinstalling linux-firmware package.

---

### Post by bigbrownepaul2 on 2013-12-04
> **Temüjin said:**
> ```
[   17.372543] r600_cp: Failed to load firmware "radeon/RS780_pfp.bin"
[   17.372555] [drm:r600_startup] *ERROR* Failed to load firmware!
[   17.372561] radeon 0000:01:05.0: disabling GPU acceleration
```

Try reinstalling linux-firmware package.


Did that no good eventually worked it out on this thread [http://ubuntuforums.org/showthread.php?t=2181190&goto=newpost](http://ubuntuforums.org/showthread.php?t=2181190&goto=newpost)

---

