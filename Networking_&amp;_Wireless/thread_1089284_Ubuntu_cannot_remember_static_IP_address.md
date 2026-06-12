---
title: "Ubuntu cannot remember static IP address"
date: 2009-03-06
forum: Networking &amp; Wireless
---

### Post by dips0502 on 2009-03-06
I am on Ubuntu 8.10 with all the latest patches...I want to assign a static IP to my ubuntu box. When I configure the network manager it works great. Upon reboot the network manager goes back to its old settings...Even the connection name changes back to Auto eth0 and status shows as never used.....

---

### Post by paddydd on 2009-03-07
I just did this and ran into a similar problem.  A google search yielded some results (here's one [http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html](http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html)) that indicate that you need to modify the /etc/network/interfaces and /etc/resolv.conf.

I don't know if you have modified these two files. 

When I set it up the first time i just changed /etc/host, host.allow and host.deny and I ran into network issues.

Good Luck,
Paddy

---

### Post by dips0502 on 2009-03-07
My /etc/network/interfaces file has only these entries -- 

auto lo
iface lo inet loopback

This is after I have put entries for static IP..

Question is why cant network manager write to these files and make it permanent.

---

### Post by cb951303 on 2009-03-07
that's a bug.

you should try to uncheck the "System setting" and "Auto connect" options in "Auto" profile until they are really unchecked. After a few try it should look like attachment 1. Then, create a new profile for static IP and check both of the options. You're set :popcorn:

---

### Post by Iowan on 2009-03-07
> **dips0502 said:**
> Question is why cant network manager write to these files and make it permanent. Network Manager stores its files in a different place - check /etc/NetworkManager/nm-system-settings.conf.

---

