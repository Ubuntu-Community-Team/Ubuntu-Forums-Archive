---
title: "ATHEROS AR9285 WLAN not working with LENOVO B560 (with ubuntu 11.04)"
date: 2012-10-02
forum: Networking &amp; Wireless
---

### Post by iosion on 2012-10-02
WTF! This solved my nasty WIFI issue with Edubuntu 12.04 on an Acer netbook. No issues on this machine with previous versions of Ubuntu, just the most recent.

What does this do?

THANKS SO MUCH!

:-)


> **chili555 said:**
> So, although I have asked you several times to blacklist acer-wmi and checked your blacklist file, it's not blacklisted, it's still loaded and it's still blocking your wireless. I want you to do the following. Please open a terminal and do:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Add a line at the very end.```
blacklist acer-wmi
```Proofread twice, save and close gedit. Now do:```
sudo gedit /etc/rc.local
```Add one line ***above*** exit 0```
rfkill unblock all
```Proofread twice, save and close gedit.

Reboot. Post back to confirm to me that every change was done perfectly as requested and to tell me how your wireless is working.

---

### Post by chili555 on 2012-10-02
> **iosion said:**
> What does this do?

It keeps the faulty module *acer-wmi* from loading and then blocking your wireless. It doesn't properly recognize and respond to key presses, Fn+F4 for wireless, for example, so the only way to get wireless is to remove it.

I think it is finally fixed in 12.04.

---

