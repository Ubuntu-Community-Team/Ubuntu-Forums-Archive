---
title: "S960 dvb-s2 usb"
date: 2015-11-23
forum: Mythbuntu
---

### Post by JohnBrines on 2015-11-23
Hi Guys,

I have installed Mythbuntu and it doesn't recognise it, no /dev/dvb . I believe it is supposed to work out of the box.

Any ideas?

---

### Post by blm-ubunet on 2015-11-23
Kernel version ?
Support only expected in 3.18 late 2014.
firmware ?
[http://www.linuxtv.org/wiki/index.php/DVBSKY_S960](http://www.linuxtv.org/wiki/index.php/DVBSKY_S960)

```
uname -r
dmesg | grep -i dvb
```

**If required**, there is the HWE stack setup for 14.04 LTS so can get later kernels without losing LTS.

---

### Post by JohnBrines on 2015-11-25
> **blm-ubunet said:**
> Kernel version ?
Support only expected in 3.18 late 2014.
firmware ?
[http://www.linuxtv.org/wiki/index.php/DVBSKY_S960](http://www.linuxtv.org/wiki/index.php/DVBSKY_S960)

```
uname -r
dmesg | grep -i dvb
```

**If required**, there is the HWE stack setup for 14.04 LTS so can get later kernels without losing LTS.

Hi Bud, sorry it took so long to get back to you as I didn't realise someone had replied as I never got an e-mail letting me know.

I got it fixed by following [http://git.linuxtv.org/cgit.cgi/media_build.git/about/](http://git.linuxtv.org/cgit.cgi/media_build.git/about/)

---

### Post by blm-ubunet on 2015-11-25
Just be aware that unless the v4l-dvb modules are setup using DKMS you'll have to rebuild & re-install (the media branch modules) with every kernel update.
It's possible the current v4l-dvb media modules have now been setup using DKMS.

---

### Post by JohnBrines on 2015-11-26
> **blm-ubunet said:**
> Just be aware that unless the v4l-dvb modules are setup using DKMS you'll have to rebuild & re-install (the media branch modules) with every kernel update.
It's possible the current v4l-dvb media modules have now been setup using DKMS.

Thanks bud will do.

Now that MythTV Backend can see the device I can't seem to scan channels :) I am going to post it on the forum.

---

