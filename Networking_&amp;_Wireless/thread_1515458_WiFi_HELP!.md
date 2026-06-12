---
title: "WiFi HELP!"
date: 2010-06-22
forum: Networking &amp; Wireless
---

### Post by donteatsoap7 on 2010-06-22
I recently had a thread ([http://ubuntuforums.org/showthread.php?t=1497562]("http://ubuntuforums.org/showthread.php?t=1497562"))
to solve my wifi problem but even though my card works now, I can't see my networks on wicd. So is there anything I could do?

---

### Post by purelinuxuser on 2010-06-22
> **donteatsoap7 said:**
> I recently had a thread ([http://ubuntuforums.org/showthread.php?t=1497562](http://ubuntuforums.org/showthread.php?t=1497562))
to solve my wifi problem but even though my card works now, I can't see my networks on wicd. So is there anything I could do?

Hi,

Please post the output of the following commands:
```
lspci
lshw -c network
iwconfig
sudo iwlist scan
```
so we can attempt to assist you. ;)

---

