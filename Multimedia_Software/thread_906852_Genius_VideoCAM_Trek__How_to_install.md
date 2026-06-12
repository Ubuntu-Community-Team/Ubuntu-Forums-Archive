---
title: "Genius VideoCAM Trek / How to install?"
date: 2008-08-31
forum: Multimedia Software
---

### Post by jorgeguberte on 2008-08-31
So, i have this webcam, "VideoCAM Trek" plugged into an USB port, but i don't have the slightest clue on how to make it work.
Is there a good soul willing to help me? :D

---

### Post by linuxwizard on 2008-09-01
Try using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Devices > Video Devices > try changing some of the settings. (try both V4L and V4L2)
 
 To test your webcam you can do this:
 There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.
 
 If Ekiga doesn't work post results of the command > lsusb

---

### Post by DisDis on 2010-01-07
Install (vid : pid 0x0C45:0x6007):
```

sudo modprobe sn9c102

```Enabled whitebalance and e.t.c:
```

# http://lwn.net/Articles/328561/
export LIBV4LCONTROL_CONTROLS=15
env LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so v4l2ucp /dev/videox

```Save to config file:
```

LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so v4l2ctrl -d /dev/videox -s ~/camera.cfg

```Load config file:
```

LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so v4l2ctrl -d /dev/videox -l ~/camera.cfg

```Skype start:
```

LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so skype

```After login, loading cam config. Work perfectly;)

---

### Post by Behemoth0089 on 2010-08-28
> **linuxwizard said:**
> Try using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Devices > Video Devices > try changing some of the settings. (try both V4L and V4L2)
 
 To test your webcam you can do this:
 There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.
 
 If Ekiga doesn't work post results of the command > lsusb

Well I have the same camera, and it works if I do this on Ekiga, but still no response at Skype.
Is there any way to make that work? 
I got Ubuntu 10.04

---

