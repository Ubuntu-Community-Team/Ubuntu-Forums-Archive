---
title: "reinstall video driver"
date: 2013-04-17
forum: Multimedia Software
---

### Post by igwt007 on 2013-04-17
I screwed up my video by installing the wrong driver how do I reset back to the default driver. Thank you.

---

### Post by dabl on 2013-04-17
With that little bit of information, it's hard to know what driver you originally had, for what model of GPU, on what Ubuntu version, or what driver you later installed.  I give this command 50% chance of fixing it -- if it doesn't, you'll need to actually provide some information.  Shutdown and reboot into recovery console, run this, then reboot and (maybe) log in normally.

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by igwt007 on 2013-04-17
I got it working by a purge command followed by installing NVIDIA current command in the terminal. Thanks anyway. By the way I'm running Ubuntu 12.10

---

