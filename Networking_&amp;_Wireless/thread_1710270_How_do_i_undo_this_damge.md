---
title: "How do i undo this damge?"
date: 2011-03-19
forum: Networking &amp; Wireless
---

### Post by c-m on 2011-03-19
Hi,

I was following this guide here
[http://forum.aircrack-ng.org/index.php?topic=5755.0](http://forum.aircrack-ng.org/index.php?topic=5755.0)

To try to patch my wifi driver.

Half way through the process failed. Just after it tells you to run "sudo rmmod r8187 rtl8187 mac80211"

Now i just want to reverse the process as now my ZTE Blade isn't detected when tethered via usb.

I got to the part just before the images. About half way down the thread.

I'm running 10.10

---

### Post by chili555 on 2011-03-19
> sudo rmmod rtl8187 zd1211rw mac80211
sudo mkdir /usr/src/drivers
cd /usr/src/drivers
sudo tar jxvf compat-wireless-aircrack-maverick-patched.tar.bz2
cd compat-wireless-aircrack-maverick-patched.tar.bz2
sudo make
sudo make install
sudo make unloadIs that about where things went all gooey? If so, please do:```
sudo rmmod rtl8187 zd1211rw mac80211
cd /usr/src/drivers/compat-wireless-aircrack-maverick-patched.tar.bz2
sudo make [COLOR="Red"]un[/COLOR]install
sudo make unload
```Reboot and give us your report.

If it was at another spot, post back and we'll help.

---

### Post by c-m on 2011-03-20
Thanks. That worked a treat

---

