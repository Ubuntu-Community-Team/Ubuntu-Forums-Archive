---
title: "Enabling wireless hardware on Amilo laptop"
date: 2010-10-17
forum: Networking &amp; Wireless
---

### Post by cfriisha on 2010-10-17
Some Amilo laptops use buttons like Fn-F10 to enable the wireless hardware. After several days of trying to fix the problem, I stumbled over [Dirk-Jan's blog]("http://www.vleeuwen.net/2009/06/wireless-fix-on-amilo-running-ubuntu"), which elegantly solved the problem:

You can check if the wireless LAN is blocked by issuing:

```
$ sudo rfkill list
```

and if you see something like "Hard blocked: yes", then the following command should enable the wireless LAN:

```
$ sudo modprobe acer_wmi
```

If this worked for you, you can make it permanent by issuing:

```
$ echo "acer_wmi" | sudo tee /etc/modules
```

where after wireless hardware will be turned on after reboot.

-------------------

In case you only use wireless occasionally, you might want to skip the last code bit and instead write a small script connected to a menu button. The case is that the wireless radio consumes power and will drain your batteries faster.

The above works for Ubuntu 10.04 as of October 2010.

---

