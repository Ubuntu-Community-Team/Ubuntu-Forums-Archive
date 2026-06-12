---
title: "Ubuntu browsing problem"
date: 2009-09-02
forum: Networking &amp; Wireless
---

### Post by mfa237 on 2009-09-02
hello to all frnds,

i have installed ubuntu on vmware workstation and its working fine, but when i try to browse any webpage with its domain address it's not working and giving error while it;s working with  IP address of websites.Kindly guide me that how can i resolve this problem.



Thanx in advance

---

### Post by hal10000 on 2009-09-02
Looks as if you have a namederver problem.
Look into the file /etc/resolv.conf (on a terminal window type [COLOR="Red"]cat /etc/resolv.conf[/COLOR]
There should be a line like
```
nameserver XXX.XXX.XXX.XXX
```
Where XXX.XXX.XXX.XXX means the ip-address of your nameserver.
How didi you setup the network interface, dhcp or static ip-address by manually editing?
If you used dhcp, then you should have obtained a nameserver ip-address and it should be written into /etc/resolv.conf automatically.
If you manually set uo your network with a static ip-address, then you have to put in the nameserver's ip-address by hand int /etc/resolv.conf

---

