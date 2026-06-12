---
title: "whatprovides /etc/modprobe.d/alsa-base"
date: 2009-01-03
forum: Multimedia Software
---

### Post by h_box on 2009-01-03
8.10

I wish to refresh to default the file /etc/modprobe.d/alsa-base.


I used "dpkg -S /etc/modprobe.d/alsa-base" to learn that alsa-base was responsible for the file in question; however re-installing alsa-base didn't replace the file. [" sudo apt-get install --reinstall alsa-base "]

I also removed alsa-base and installed fresh, still it has not touched the file. I tried deleting the file and re-installing alsa-base and still no file. I have also tried alsa-utils.

1. Is /etc/modprobe.d/alsa-base actually part of alsa-base?
2. Does some configuration script need to be instantiated to create /etc/modprobe.d/alsa-base?

Thanks very much for your info.

---

### Post by cariboo on 2009-01-03
When you uninstall alsa-base are you doing it from a terminal and using the purge option eg:

```
sudo apt-get purge alsa-base
```

The above command will completely remove alsa-base and all its configuration files.

Jim

---

### Post by h_box on 2009-01-04
Thanks, after the purge and reinstall, the file is there.

Best,

JH

---

