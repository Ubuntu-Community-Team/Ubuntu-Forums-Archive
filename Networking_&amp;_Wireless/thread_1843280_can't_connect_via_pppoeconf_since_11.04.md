---
title: "can't connect via pppoeconf since 11.04"
date: 2011-09-13
forum: Networking &amp; Wireless
---

### Post by Anuovis on 2011-09-13
Hello,

I have a moderate problem of not being able to connect to the internet. I could provide technical details but it seems that either something is wrong with my internet provider (not likely though), or something changed with the release of Ubuntu 11.04

I have been connecting to the internet for a few years and my hardware setup is exactly the same to this day, even the cables. I would run sudo pppoeconf with Ubuntu 9.10 or 10.04 and that was enough. Now, however, it doesn't work any more.

My ISP doesn't support Linux so I am on my own here. Could it be that the newer Ubuntu has troubles recognizing or utilizing my eth0?

I'm really confused, don't even know where to start looking. Any help would be really appreciated.

---

### Post by realzippy on 2011-09-13
what happens when you run

```
pon dsl-provider
``` ?

---

### Post by praseodym on 2011-09-13
Hi,

add yourself to the group "dip":

```
sudo adduser $USER dip
```
deactivate the network-manager in "autostart" and login again. After that execute

```
sudo pppoeconf
```

again. Maybe you need to uninstall the network-manager completely:

```
sudo apt-get remove --purge network-manager network-manager-gnome
```
Can you show:

```
cat /etc/network/interfaces
cat /etc/resolv.conf
ifconfig -a
```

---

### Post by Anuovis on 2011-09-14
I am very sorry, this was probably some technical issue with my ISP. Today I noticed that the connection works like before and was able to get on the net via pppoeconf.

Their support line told me the connection settings were to blame but apparently that wasn't the case.

Marking as solved since the problem is gone.

---

