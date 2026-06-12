---
title: "Anybody know the current state of flash hw acceleration in linux?"
date: 2010-08-28
forum: Multimedia Software
---

### Post by tjones00 on 2010-08-28
Out of curiosity I was wondering if adobe 10.1 beta in linux now supports hardware acceleration?

Most of my googles on this topic refer me to comments made years ago.

If the adobe player still doesn't support hardware acceleration has any open source player provided support yet?

---

### Post by tjones00 on 2010-08-28
I hate answering my own question but.

[http://www.devicemag.com/2010/06/10/adobe-flash-10-1-with-gpu-hardware-acceleration-support-now-available/](http://www.devicemag.com/2010/06/10/adobe-flash-10-1-with-gpu-hardware-acceleration-support-now-available/)

Suggests linux is now supported as of June 10th.

Current release notes. I think it's for version 10.1.83.

[http://kb2.adobe.com/cps/838/cpsid_83808.html](http://kb2.adobe.com/cps/838/cpsid_83808.html)

Has anybody tried the latest player on a nvidia ion yet and can they confirm hw acc?

I'd try it but I'm not running a standard desktop/firefox etc on my ion platform.

---

### Post by mikewhatever on 2010-08-28
This article is fairly recent:
[http://www.phoronix.com/scan.php?page=news_item&px=ODEyOQ](http://www.phoronix.com/scan.php?page=news_item&px=ODEyOQ)

---

### Post by lovinglinux on 2010-08-28
[According to Adobe]("http://blogs.adobe.com/penguinswf/2008/05/flash_uses_the_gpu.html"), Flash is fullscreen GPU accelerated since version 9.0.115.0.

The problem is that it doesn't work with Compiz, it doesn't use xv and it doesn't work if the content is not authored to make use of hardware acceleration.

I guess those articles mentioned above are only referring to H.264 acceleration, which is the case for HD YouTube videos.

---

