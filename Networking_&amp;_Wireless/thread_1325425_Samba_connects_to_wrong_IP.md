---
title: "Samba connects to wrong IP"
date: 2009-11-13
forum: Networking &amp; Wireless
---

### Post by Thelasko on 2009-11-13
I am trying to connect two Ubuntu machines via Samba.  One is a Hardy Heron desktop machine and the other is a Karmic Mythbuntu laptop.  When I try to connect the desktop to the laptop it appears to connect to an IP address that isn't on my network (208.69.34.132, an OpenDNS server).  However, the correct address is a local one (192.168.1.xxx).  

If I enter smb://192.168.1.xxx into nautilus it works.  Anybody have any idea why this is happening?  Is Samba trying to resolve the host name via OpenDNS.  It's set to look at lmhosts first.

---

### Post by spd106 on 2009-11-13
Can you see the host by using nmblookup?

If not then you will need to check that Netbios is set-up correctly.

Useful link:
[http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/integrate-ms-networks.html](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/integrate-ms-networks.html)

Hope that helps.

---

### Post by puppywhacker on 2009-11-13
you might consider making samba server on your laptop to only listen to the internal network.

in /etc/samba/smb.conf
```
interfaces = 192.168.1.0/24
```

It is ultimately up to the order of the name resolving that get the name translated into the wrong ip-address. By default the resolve order is

```
name resolve order = lmhosts host wins bcast
```

which means that first the /etc/lmhosts, than the /etc/hosts than the wins server and than a broadcast is used to identify the samba name. This order is different than your normal internet resolving set in /etc/resolv.conf

---

