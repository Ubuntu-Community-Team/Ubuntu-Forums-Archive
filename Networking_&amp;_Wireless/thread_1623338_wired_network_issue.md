---
title: "wired network issue"
date: 2010-11-16
forum: Networking &amp; Wireless
---

### Post by alphaace on 2010-11-16
Hi,

I am using Ubuntu 10.04. 

Recently my wired connection no longer connects. I know my cable is good because I tested it on my laptop.

When I go to Devices - Network Toos, for my ethernet interface, I see an IPv6 IP but not an IPv4. What's going on? Any help would really be greatly appreciated. Thank you!

---

### Post by ajgreeny on 2010-11-16
Right click on your network icon in the panel and go to "Edit connections".

Have a look in the tabs for ipv4 and ipv6.  ipv4 should probably be Automatic (DCHP) and ipv6 probably will be ignore, but it is certainly the ipv4 which may have changed for some reason.  I am assuming, of course, that your connection from router or modem is set to DCHP as most are by default.

---

