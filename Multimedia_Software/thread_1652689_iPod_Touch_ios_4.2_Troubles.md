---
title: "iPod Touch ios 4.2 Troubles"
date: 2010-12-25
forum: Multimedia Software
---

### Post by Joe8095 on 2010-12-25
Hello,

I updated my ipod touch 4g to ios 4.2.1, and now it will not mount properly.  Whenever I plug it in, the camera mounts but nothing else.  It also will not mount in Rhythmbox. I have updated libimobiledevice to version 1.0.4, and I am running Ubuntu 10.10 x86.  I have read in the forums that running ```
idevicepair unpair
idevicepair pair
idevicepair validate
```fixes the problem, but when I try it I get
```
$ idevicepair unpair
usbmuxd_get_device_list: error opening socket!
No device found, is it plugged in?
```Does anybody know what is causing this problem?

Thank you very much!

---

### Post by Rustybike on 2011-01-05
I had the same issue.  I found that when I updated "usbmuxd 1.05" in Synaptec Packet Manager (for some reason 1.06 and 1.05 were both installed), I was able to then successfully use idevicepair as stated, and then add music to my new iPod Touch with Rhythmbox.

---

