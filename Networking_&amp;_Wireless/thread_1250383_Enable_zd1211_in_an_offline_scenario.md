---
title: "Enable zd1211 in an offline scenario"
date: 2009-08-26
forum: Networking &amp; Wireless
---

### Post by narcisgarcia on 2009-08-26
I've an Ubuntu GNU/Linux 9.04 Live-CD and a computer with an operating MSWindows that connects to internet with a "Amper WN4501H" USB wireless stick.
Before installing Ubuntu, I'm trying to get connected to internet with the Live-CD using the same USB antenna. There is no other way to connect to internet in that house, and cannot move the computer.

Searching in internet I've found that this WN4501H is based on zd1211, and I've tried to enable it with this command:
```
sudo modprobe zd1211rw
```
...but the network-manager doesn't mention anything about wireless.

I can't use the source from [http://sourceforge.net/projects/zd1211/](http://sourceforge.net/projects/zd1211/) and compile the driver, because I can't download the kernel and build packages to make a compilation (I'm offline).

I've tried to download in MSWindows the zd1211-firmware package from Debian 5.0, but Gdebi doesn't install and shows an error.

Any ideas?

---

### Post by narcisgarcia on 2009-08-26
I've seen also this source package for Jaunty:
[https://launchpad.net/ubuntu/jaunty/+package/zd1211-source](https://launchpad.net/ubuntu/jaunty/+package/zd1211-source)

But I don't know how to compile it offline!!

---

