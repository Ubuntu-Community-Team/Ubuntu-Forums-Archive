---
title: "cannot get wl.ko to load on boot"
date: 2013-01-12
forum: Networking &amp; Wireless
---

### Post by miatawnt2b on 2013-01-12
I cannot seem to get the wl driver to load on boot.  Every time I reboot lsmod shows brcmsmac loaded instead.

I've installed/reinstalled the bcmwl-kernel-source package.
'modprobe wl' will load the driver
depmod -a

the wl.ko module is in /lib/modules/3.5.0-19-generic/updates/dkms/

/etc/modprobe.d/blacklist.conf contains the following:
blacklist ssb
blacklist bcma
blacklist b43

why will wl load manually, but every reboot the brcmsmac driver is installed instead?
-J

---

### Post by miatawnt2b on 2013-01-13
bumping this up... every time I boot I run the following:
```

rmmod brcmsmac
rmmod bcma
rmmod brcmutil
rmmod mac80211
rmmod cfg80211
rmmod cordic
modprobe wl

```

I have tried blacklisting every driver that I rmmod above... still won't load wl on boot.

-J

---

### Post by mikewhatever on 2013-01-13
Have you tried blacklisting brcmsmac? ...and to make sure wl auto-loads, add it to /etc/modules.

---

