---
title: "Please help activate Broadcom BCM4312 after upgrade to 12.04"
date: 2012-12-31
forum: Networking &amp; Wireless
---

### Post by T C on 2012-12-31
I have a Broadcom BCM4312 wireless adapter in a 32-bit Dell notebook. After the upgrade to Ubuntu 12.04, it no longer works. I've seen many threads on this forum dealing with Broadcom wireless problems, but I haven't found a solution among them.

When I go to "Additional Drivers" and attempt to activate "Broadcom STA wireless driver", I get a message saying "Sorry, installation of this driver failed". The log file says something like this:

```
2012-12-31 07:07:39,496 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl
2012-12-31 07:07:39,496 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2012-12-31 07:07:39,559 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
```When I try to install bcmwl-kernel-source, I get something like this:
```
tc@LAGOON:~$ sudo apt-get install linux-headers-generic bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-generic is already the newest version.
bcmwl-kernel-source is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
tc@LAGOON:~$ sudo modprobe wl
FATAL: Module wl not found.
FATAL: Error running install command for wl
tc@LAGOON:~$ 
```Can anyone suggest what I might try next?

-TC

---

### Post by lykwydchykyn on 2012-12-31
Try running:
```

sudo dpkg-reconfigure bcmwl-kernel-source

```

To see if it will recompile the driver for you.  Maybe make sure dkms is installed first, though I assume it's a dependency.

I have trouble with the wl driver on my BC4312 (also a Dell).  I switched to using the b43 driver.  If the above doesn't give you a wl driver, try:
```

modprobe b43

```
And see if your wireless works.

---

### Post by T C on 2012-12-31
Your suggestion worked. This activated the adapter:

```
sudo dpkg-reconfigure bcmwl-kernel-source
sudo modprobe wl
```

Thanks.
-TC

---

