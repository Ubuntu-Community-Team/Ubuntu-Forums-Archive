---
title: "aplay -l no soundscards found..."
date: 2014-11-13
forum: Multimedia Software
---

### Post by jason_lee2 on 2014-11-13
Hi guys I recently got a new work computer with Ubuntu 10.04. However I can't get any sound. The horn icon doesn't show on my tray, and I got nothing under "Hardware" in sounds setting. Here is some detail information:

uname -a
```
Linux XXXXXXX 2.6.32-67-generic #134-Ubuntu SMP Wed Sep 24 18:45:40 UTC 2014 x86_64 GNU/Linux
```

aplay -l
```
aplay: device_list:223: no soundcards found...
```

cat /proc/asound/version
```
cat: /proc/asound/version: No such file or directory
```

lspci | grep Audio
```
00:03.0 Audio device: Intel Corporation Device 0c0c (rev 06)
00:1b.0 Audio device: Intel Corporation Device 8c20 (rev 05)
```

Could anyone please give me some suggestion about how I can fix it? I googled but every case seems different so I figured just ask... Thank you so much!

---

### Post by TheFu on 2014-11-13
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases) - 10.04 desktop support ended May 2013.
Tell your IT department it is over a year out of support and that you need an upgrade to a supported release, like 14.04 LTS.

---

