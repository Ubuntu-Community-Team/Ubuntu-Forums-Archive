---
title: "Repeat of DHCPOFFER and DHCPNAK"
date: 2006-06-29
forum: Networking &amp; Wireless
---

### Post by oberoc on 2006-06-29
Hi Everybody,

    I have a problem connecting to my apartment's LAN. I do a 
/etc/init.d/networking restart
and I get
DHCPOFFER
DHCPNAK
DHCPREQUEST
DHCPNAK
DHCPREQUEST
DHCPNAK
....
DHCPOFFER
etc....

I also did a tcpdump -v -i eth0 and did indeed see a offer come from the server, but my machine isn't picking it up. I am using the e100 driver. The particular model of my machine is a Thinkpad a31. If you need anymore information, please ask.

---

