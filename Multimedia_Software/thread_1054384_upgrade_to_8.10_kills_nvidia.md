---
title: "upgrade to 8.10 kills nvidia"
date: 2009-01-29
forum: Multimedia Software
---

### Post by ghostandmachine on 2009-01-29
So I updated from 8.04 to 8.10 and the new nvidia-glx-177 was installed.

Well my login screen gave me the res I'm use to (1680x1050) but after the login my monitor went black and I received the error "Cannot Detect Display"

Going back into recovery mode using xfix gave me a desktop but only at 800x600.

Under the hardware drivers, it says that nvidia 177 is activated but when I go into nvidia-settings it says that I'm not running a nvidia driver.

dpkg-reconfigure -phigh xserver-xorg doesn't do much except give me more specs on my xorg.conf file than the xfix does.

---

### Post by cariboo on 2009-01-29
Make sure that when you upgraded, that you got the latest xserver-org and kernel, as you need both in order to compile the Nvidia drivers.

```
xserver-xorg v. 1:7.4~5ubuntu3
Linux-iamge v. 2.6.27.X
```

Jim

---

### Post by ghostandmachine on 2009-01-30
how would i go about installing/checking those? through synaptic?

---

