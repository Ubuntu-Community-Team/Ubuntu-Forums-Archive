---
title: "Trendnet 424 + NDISwrapper not working"
date: 2009-07-04
forum: Networking &amp; Wireless
---

### Post by avrilrox on 2009-07-04
Hey guys, I'm really stuck with this usb wifi adapter called "Trendnet 424 UB". I think it's v3.

I've been basically using this thing for the last year and it worked flawlessly under **Hardy Heron 32 bits**. In order to get this to work, i used the **net8187b** driver, which i got from the trendnet site. Window$ XP 32 bit drivers worked perfectly well.

However,I just did a clean install of the stable version of Jaunty **64 bits** and it's not working. I installed ndiswrapper 1.53 and ndiswrapper-utils1.9.

I did a blacklist on the default driver rtl8187 by adding a line like this to my /etc/modprobe.d/blacklist file:
```
blacklist rtl8187
```

I did a rmmod rtl8187 but when i do a ndiswrapper -l it says:

```
net8187b : driver installed
             device (0BDA:8189) present (alternate driver: rtl8187)
```

I keep removing and installing my driver but it still keeps saying that the alternate driver is being used. I rebooted several times and still no luck.

This is the output of iwconfig:

```

lo       no wireless extensions
eth0     no wireless extensions
pan0     no wireless extensions

```

Any ideas?

---

### Post by avrilrox on 2009-07-05
Isn't there any patches for the rtl8187 driver? I can't get ndiswrapper to use the net8187b

---

### Post by avrilrox on 2009-07-05
Alright. I've tried 32 bit drivers and when i check dmesg it says that drivers are 32 bits and the system is a 64 bit one but if i install 64 bit drivers ubuntu just hangs and gets stuck at the login window when i enter my username and password.

Any ideas?

---

