---
title: "Sound works for root but not for other users"
date: 2006-08-05
forum: Multimedia &amp; Video
---

### Post by Nesnej Trick on 2006-08-05
For some reason my Ubuntu 6.06 installation recognizes the sound card only when logged in as root. When logged in as root the command ```
$ aplay -l
``` returns:

```
**** List of PLAYBACK Hardware Devices ****
kort 0: CK804 [NVidia CK804], enhet 0: Intel ICH [NVidia CK804]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
kort 0: CK804 [NVidia CK804], enhet 2: Intel ICH - IEC958 [NVidia CK804 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

For any other user it returns 
```
aplay: device_list:221: no soundcard found... 
```

First I thought I didn't have the drivers installed, and I installed the proper driver for the Realtek ALC850 codec on this ASUS A8N5X. However, doing that broke libasound.so.2, barring me from GNOME, so I had to reinstall libasound2 from failsafe mode.
Evidently the driver is there, but for some reason it's not found when logged in as any other user than root.

Any ideas what to do?

---

### Post by Nesnej Trick on 2006-08-06
Nevermind, it turned out I hadn't ticked "allow user to: use sound units" in System > Administration > Users and Groups > Properties. ](*,) Fairly basic but easily forgotten. It's all working now. :cool:

---

