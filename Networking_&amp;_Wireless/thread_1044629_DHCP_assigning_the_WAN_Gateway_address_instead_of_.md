---
title: "DHCP assigning the WAN Gateway address instead of configured pool"
date: 2009-01-19
forum: Networking &amp; Wireless
---

### Post by asbesto on 2009-01-19
Hi everybody, here's a very weird problem

dhclient in my eeepc seem not working in a very strange way.

I configured a pool of IP from 10.69.1.150 to 10.69.1.170 on my DHCP server, and is correctly working because I use it on many laptops here. 

But on my eeepc, here's what I obtain:

> 

root@lem:~# dhclient
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/wifi0/
Sending on   LPF/wifi0/
Listening on LPF/eth0/00:1e:8c:e5:19:ff
Sending on   LPF/eth0/00:1e:8c:e5:19:ff
Listening on LPF/ath0/00:15:af:77:f8:cf
Sending on   LPF/ath0/00:15:af:77:f8:cf
Sending on   Socket/fallback
DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 6
**DHCPREQUEST of 84.223.128.219 on eth0 to 255.255.255.255 port 67**
DHCPREQUEST of 84.222.225.31 on ath0 to 255.255.255.255 port 67
**DHCPACK of 84.222.225.31 from 10.69.1.1**
bound to 84.222.225.31 -- renewal in 1001460 seconds.





84.222.225.31 is my ADSL GATEWAY!

what the hell is going on? this is drivin me nuts!

:confused:

---

### Post by jonobr on 2009-01-19
Hi!

Just curious, whats the eeepc?

Also, it just sounds as if you have two DHCP servers running on the one lan,
your ADSL router is responding with addresses from its DHCP pool before your server.

In the bootup, the machine will send a broadcast to all for an IP address , so im thinking if you set it up so your DHCP answers with address based only on mac address, may that help?

---

### Post by Iowan on 2009-01-19
eeepc is Asus netbook computer - my son has one.  

It almost looks like the eee is *requesting* that IP address (via eth0?)

---

### Post by asbesto on 2009-01-19
I forgot: my DHCP server IS the ADSL Router. Is the same device!

And on other laptops it work very fine. :(

---

### Post by Iowan on 2009-01-19
What's in */etc/dhcp3/dhclient.conf*?

---

### Post by asbesto on 2009-01-20
only this in my /etc/dhcp3/dhclient.conf:


> send host-name "<hostname>";
request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, domain-name-servers, host-name,
        netbios-name-servers, netbios-scope;
timeout 30;



everything else is commented out via "#"...

---

### Post by Iowan on 2009-01-20
I'm still a little fuzzy on whether "<hostname>" is supposed to insert hte current hostname, or if it's just a placeholder.  Although it will probably make no difference, you might comment out that line - or replace <hostname> with the actual hostname.

---

### Post by asbesto on 2009-01-21
Tried that, but the problem is still there :!

also, clearing leases in /var/lib/dhcp3 doesn't solved.

Changed mac address of my wifi card, no way.

I will kill myself. sure.

---

### Post by Iowan on 2009-01-21
> **asbesto said:**
> I will kill myself. sure.Not yet...
I'm still curious where the following lines come from:> DHCPREQUEST of 84.223.128.219 on eth0 to 255.255.255.255 port 67
DHCPREQUEST of 84.222.225.31 on ath0 to 255.255.255.255 port 67

(Just thinking out loud - so to speak)

---

### Post by asbesto on 2009-01-22
Really I don't know. I still have this problem, anyway :(

---

