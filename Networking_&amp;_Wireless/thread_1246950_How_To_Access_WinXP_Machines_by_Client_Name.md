---
title: "How To Access WinXP Machines by Client Name"
date: 2009-08-22
forum: Networking &amp; Wireless
---

### Post by DeskRocket on 2009-08-22
I have set up a Bacula server on Ubuntu and I'm in the process of configuring it.

I would like to refer to the WinXP clients by machine name rather than IP.

Assuming I have an XP client named FRONT_DESK with ip 192.168.1.100, I can ping successfully 192.168.1.100 from my Ubuntu server but ping of FRONT_DESK (or front_desk) times out.

Where should I start looking?

Best regards,
Alan

---

### Post by Iowan on 2009-08-22
You can modify */etc/hosts* to associate machine name and IP address... assuming the machines have static addresses. The other alternative would be to have a local DNS server (**dnsmasq**?).

---

### Post by DeskRocket on 2009-08-22
Thanks! I'll modify */etc/hosts.* That will give me one more level of flexibility.

Best regards,
Alan

---

