---
title: "DHCP only for Authenticated Users(AD users)"
date: 2011-04-04
forum: Networking &amp; Wireless
---

### Post by mkhurram92 on 2011-04-04
hi all there,

i have a Domain Cotroller installed on Windows & DHCP Server installed on Ubuntu. i want to give access only authenticated Users(Active Directory Users) can get IP from DHCP. No one else can 
is there any option available here in DHCP ???

---

### Post by regala on 2011-04-04
> **mkhurram92 said:**
> hi all there,

i have a Domain Cotroller installed on Windows & DHCP Server installed on Ubuntu. i want to give access only authenticated Users(Active Directory Users) can get IP from DHCP. No one else can 
is there any option available here in DHCP ???

short answer: no. because it is nonsense. as many people as you wish can use a computer host. and a user can use as many computers as she wants.

long answer: this has got nothing to do with DHCP which must be a simple protocol. you have to use EAP style AAA (authentication, authorization, accounting) to enable/disable a physical port on your switching equipment depending on correct authentication. then the carrier is enabled on the network link, and the DHCP request can be emitted.

This is exactly how WPA2 Enterprise works.

---

### Post by SeijiSensei on 2011-04-04
You can control which MAC addresses will be given an IP address in dhcpd.  If users are generally on the same machines all the time, that's the best you can do.

Why aren't you running DHCP on the AD server?  Perhaps that would offer the solution you seek?

regala is right, though. Because Linux is inherently multi-user, someone other than the logged-in user sitting in front of the screen could be using a Ubuntu host remotely via SSH or X-forwarding.

---

