---
title: "Release / Renew IP and nameservers change not working"
date: 2009-09-17
forum: Networking &amp; Wireless
---

### Post by Szise on 2009-09-17
I'm trying to renew my IP address but is not possible.     I tried:  Uninstalled Network Manager   sudo gedit /etc/network/interfaces    added:   auto eth0 iface eth0 inet dhcp   sudo /etc/init.d/networking restart    Isn'tworking, tried:  ifdown eth0  in /var/lib/dhcp3 deleted all content from dhclient.eth0.leases AND dhclient.leases  ifup eth0  but isn't working.  tried:  sudo dhclient -r  sudo dhclient  Tried to use OpenDNS nameservers:   sudo gedit /etc/dhcp3/dhclient.conf  added: prepend domain-name-servers 208.67.222.222 208.67.220.220;  tried  sudo gedit /etc/resolv.conf  added the nameservers:   nameserver 208.67.222.222 nameserver 208.67.220.220  typed: sudo chattr -i /etc/resolv.conf   but nothing, always the default settings are restored.   How to renew my IP, change nameservers?  Note: in XP worked, in Debian the IP was dynamic when i tried, changing all the time.

---

### Post by wojox on 2009-09-17
Try:

```
sudo dhclient -r
```

Force the lease to expire.

Then:

```
sudo dhclient
```

Obtain a new lease.

---

### Post by Szise on 2009-09-17
How to force the lease to expire? because by typing only those commands isn't working.

---

