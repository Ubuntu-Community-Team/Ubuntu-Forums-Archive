---
title: "Skype - Video not working"
date: 2009-09-05
forum: Multimedia Software
---

### Post by polt on 2009-09-05
Hello,

I've just gotten a Logitech Quickcam Communicate MP.  I'm trying to use it on Skype, and the sound works, but there is no video output.  People who I call cannot see me.  In the video preferences in skype, I've already selected the UVC camera, which is the only option.  

Does anyone know of any solutions to this problem?  Most of the video related Skype solves I've seen are related to other issues, so hopefully the answer isn't up already.

Thanks!

Polt

p.s. I'm using Ubuntu, gnome, Jaunty.

---

### Post by nikgare on 2009-09-06
To get my video working in the new skype I had to start it using this program:
```

#!/bin/sh
wait 2
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype

```

---

### Post by polt on 2009-09-06
Hm.  So, I tried to run that, and received the following error:

```

ERROR: ld.so: object '/usr/lib32/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.

```

---

### Post by nikgare on 2009-09-06
Try lookig here:
[http://ubuntuforums.org/showthread.php?t=997807](http://ubuntuforums.org/showthread.php?t=997807)

---

### Post by polt on 2009-09-09
Thanks!  That worked magnificently.:popcorn:

---

