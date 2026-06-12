---
title: "Changing default dhcp client"
date: 2006-03-08
forum: Networking &amp; Wireless
---

### Post by ljrmorgan on 2006-03-08
For some reason, on my uni network dhclient does not get assigned an IP address. Quite a few people have experienced this, however the dhcp**c**d client does get an IP address.

I compiled dhcpcd, and can get an IP address by typing "dhcpcd eth0", but ubuntu still tries to use dhclient at startup and when I run ifup, etc. I edited the /etc/network/interfaces file to use the dhcpcd client as the default, but for some reason this hasn't changed anything.

Does anyone know how to make dhcpcd the default instead of dhclient?

Note: I'm talking about dhcpcd, not the dhcpd server.

Thanks,

Louis

---

### Post by Lambert on 2006-03-08
I'm not sure what script calls on dhclient during boot.

Maybe not proper but as a quick fix suggestion, you could create a symlink from /sbin/dhclient to /sbin/dhcpd. (you'll want to check on location of dhcpd as this may not be correct)

You might want to wait to see if someone else has another way.

---

### Post by steve196 on 2006-03-09
I have the same scenario. Changing that link doesn´t do anything.

---

### Post by steve196 on 2006-03-09
[http://www.scrounge.org/linux/dhcpcd.html](http://www.scrounge.org/linux/dhcpcd.html) has a description for redhat. I don´t know, how to translate that though.

---

### Post by steve196 on 2006-03-09
Though considerably slower than in Windows, the internet works now. Here is what I did:

sudo dhcpcd eth0
sudo dhcpcd start eth0
(now the nameserver is pingable but not recognized for what it is)
(open network control panel, activate LAN and enter nameservers)
(ping stops working now)
(again)
sudo dhcpcd eth0
sudo dhcpcd start eth0
(Now there is internet with DNS.)

I do not know how to make the computer do that at boot time.

---

