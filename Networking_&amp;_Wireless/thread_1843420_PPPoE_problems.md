---
title: "PPPoE problems"
date: 2011-09-13
forum: Networking &amp; Wireless
---

### Post by HH60Gunner on 2011-09-13
Hi,

I'm trying to setup PPPoE in Ubuntu.  Where I am at it work fine under my windows but I just can't seem to get it to work in ubuntu.  I've configured pppoe using the sudo pppoeconf command and I get the PPP0 under ifconfig.  It shows an address and looks active, however when I try to browse the internet I get nothing.  What gives?  Also I won't be able to install anything because without getting on PPPoE I can't get on the internet over here in Afghanistan.  Any help on resolving this issue would be greatly appreciated.

---

### Post by dineshs on 2011-09-13
please post the results of```
cat /etc/resolv.conf
``````
ifconfig -a
```and```
ping 4.2.2.1 -c4
```

---

### Post by praseodym on 2011-09-13
Deactivate the network-manager or uninstall it with

```
sudo service network-manager stop
sudo apt-get remove --purge network-manager network-manager-gnome
sudo adduser $USER dip
```login again and try

```
sudo pppoeconf
```

again

---

