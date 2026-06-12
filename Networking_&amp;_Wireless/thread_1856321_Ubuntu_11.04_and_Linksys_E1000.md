---
title: "Ubuntu 11.04 and Linksys E1000"
date: 2011-10-08
forum: Networking &amp; Wireless
---

### Post by bovisrex on 2011-10-08
Alright, I've tried a few solutions that I saw on this page and no dice. I currently have a Windows 7 desktop and a Compaq CQ62 Laptop running Ubuntu 11.04. Up until last week, both ran fine on cable broadband through Brighthouse networks in Florida; additionally, I haven't had problems connecting the laptop at various public WiFi spots. Now I live in Atlanta, and today I got Comcast 20mbps service into my house. The Windows box works fine wired into the router (I haven't been able to try it on wireless yet). Same with the laptop. But now, it doesn't want to connect wirelessly. It will connect to the router just fine, but it won't go out on the Internet. (Occasionally, right after a reboot, I'll be able to go to one or two sites, and then it stops working, though it still shows it connected to the router.) I've tried this script:

sudo ifconfig eth0 down
sudo ifconfig eth0 192.168.1.2 up
firefox 192.168.1.1

and no dice.

Any ideas?

Thanks!

Chris

---

### Post by praseodym on 2011-10-08
Hi,

please show:

```
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
sudo iwlist scan
```

---

