---
title: "Specifying what interface to listen on for dhcp"
date: 2009-06-24
forum: Networking &amp; Wireless
---

### Post by acm321 on 2009-06-24
Hi. I'm currently using an Ubuntu box as a router using eBox, and everything works like it should, except that I cant seem to set up a DHCP server. The syslog tells me that I haven't specified what network interface that the DHCP server should listen on. I want it to listen on eth1, how can I configure it to do so?

Thanks.

---

### Post by alastair on 2009-06-24
ISC dhcpd doesn't seem to have a "listen" style option (although I know dnsmasq DHCP does). What DHCP does ebox use? What's the actual error message?

---

### Post by acm321 on 2009-06-24
I'm not sure what DHCP ebox uses, but it's fixed now somehow, and everything works.
Thanks anyway! =D

---

