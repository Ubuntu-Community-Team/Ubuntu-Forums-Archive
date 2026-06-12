---
title: "renewal time for dhcp"
date: 2011-01-17
forum: Networking &amp; Wireless
---

### Post by mahmoodn on 2011-01-17
I get this information by running "dhclient":
```
mahmood@localhost:~$ sudo dhclient
[sudo] password for mahmood:
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth0/00:1f:d0:6f:38:89
Sending on   LPF/eth0/00:1f:d0:6f:38:89
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPOFFER of 192.168.100.28 from 192.168.100.3
DHCPREQUEST of 192.168.100.28 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.100.28 from 192.168.100.3
bound to 192.168.100.28 -- renewal in [COLOR="Red"]364 [/COLOR]seconds.

```
As you can see, the renewal time is very short and I found regular and periodic disconnection. How can I increase that value?
Thanks

---

### Post by Iowan on 2011-01-17
*/etc/dhcp3/dhclient.conf* has an option to ```
#send dhcp-lease-time 3600;

```but the DHCP server *should* have an option to adjust lease times, too.

---

### Post by mahmoodn on 2011-01-17
should I remove the comment? or this the syntax of that file?

---

### Post by Iowan on 2011-01-17
I just copied that line from my machine - it'd need the comment removed to take effect. 
Do you have a way to check settings on DHCP server? Is it only this machine that has a problem?

---

### Post by mahmoodn on 2011-01-18
No I don't access to dhcp server. However I will try what you said.

---

