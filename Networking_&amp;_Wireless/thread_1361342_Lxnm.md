---
title: "Lxnm"
date: 2009-12-21
forum: Networking &amp; Wireless
---

### Post by chessnerd on 2009-12-21
So I recently put LXDE on my desktop and I have been impressed with it so far, but I have run into an issue with the network manager.

I installed LXNM and it took over for network-manager (even uninstalled it) and then I configured it by setting it to use eth1 (via the lxpanel network icon) and then inputing these commands:

```
sudo ifconfig eth1 up
sudo dhclient eth1
```

Now I need to do this every time the system boots up to get it to work because eth0 is the default that it looks for and, because the eth0 port doesn't work under Windows, I use the eth1 port. Is there any way to set eth1 as the default in LXNM?

---

### Post by kerry_s on 2009-12-21
in /etc/udev there's a file for the detected network devices, you just need to change the assignment from "eth0" to "eth1".

sorry i'm not on linux so i can't be exact.

---

### Post by chessnerd on 2009-12-21
Thank you for you help. The file was in /etc/udev/rules.d and was called "70-persistent-net.rules". I just switched around the names for the eth0 and eth1 devices and, after editing the /etc/network/interfaces file to correct for the change it worked.

---

