---
title: "hostap and bridges"
date: 2010-03-31
forum: Networking &amp; Wireless
---

### Post by bakegoodz on 2010-03-31
I have a wireless gateway that works great, uses Ubuntu 10.04, hostapd, and using a nl80211 based wireless driver (rt61 pci card). Works beautifully, but I'm having trouble making it a wired gateway too. When I try to bridge it to an Ethernet interface, it all goes to hell and the wireless no longer works.
 I tried this by adding bridge_ports wlan0 eth1, changing the appropriate interface names from wlan0 to br0. Also uncomment the bridge=br0 line in hostapd.conf Anybody made this work or know any good guides online?

---

### Post by Bungler on 2010-03-31
I used these:

[https://help.ubuntu.com/community/Router](https://help.ubuntu.com/community/Router)
[http://ubuntulinuxhelp.com/how-to-setup-a-wireless-ubuntu-router/](http://ubuntulinuxhelp.com/how-to-setup-a-wireless-ubuntu-router/)

As guidelines, but actually I can not help you because I have exactly the same problem! I know there is more to it then just make a bridge, also the right packets should be forwarded.
In any case, I joined this topic because I would like to know as well...

---

### Post by bakegoodz on 2010-03-31
I figured out how to masquerade to two interfaces, so it working with the wired and wireless on their own lan.

---

### Post by Bungler on 2010-04-01
This morning I struggled with my own (similar) issues a bit and it seems for me the bridging was not necessary, I just created a network (ad-hoc wireless in my case) and then directly used packet forwarding and it worked. Creating a bridge was not required. Perhaps it works for you as well?

---

