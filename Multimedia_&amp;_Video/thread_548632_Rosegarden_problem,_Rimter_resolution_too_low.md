---
title: "Rosegarden problem, Rimter resolution too low"
date: 2007-09-11
forum: Multimedia &amp; Video
---

### Post by paparappa on 2007-09-11
I've searched the forums but they have actually not been to any help for me. So i decided to start my own thread.

When i start rosegarden there comes an error message that tells me "System timer resolution is too low" (look here: [http://pici.se/pictures/fWmTCqdXN.png](http://pici.se/pictures/fWmTCqdXN.png) )

What can i do to fix this? (Im a ubuntu noob so keep it simple.)

---

### Post by stmiller on 2007-09-11
The stock kernel Ubuntu uses is not good for audio and video work. If you are using a standard 32bit or 64bit Ubuntu distro, install this kernel:
```

sudo apt-get install linux-lowlatency linux-image-lowlatency

```

and reboot.

This kernel has an increased kernel timing setting, and enables a low-latency kernel. The other option is to compile your own kernel and make the change in configuring the kernel. :popcorn:

---

