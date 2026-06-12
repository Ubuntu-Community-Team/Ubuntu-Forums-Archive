---
title: "how to turn off IPv6"
date: 2010-01-14
forum: Networking &amp; Wireless
---

### Post by chillyomi on 2010-01-14
can some one please explain to me how to turn off the default IPv6 so I can change to IPv4 on 9.10 Jaunty

---

### Post by gabo.cr on 2010-01-14
I only know how to disable Ipv6 by default using Firefox.
Type this on the web browser:

> about:config

The search for:

> network.dns.disableIPv6

Set it to TRUE

---

### Post by PRC09 on 2010-01-14
I believe you can also disable it from the network icon on the task bar.Right click the icon, select edit connections,select your connection,select edit and disable from there.I dont think IPV6 is enabled by default tho.This applies to 9.10 as my 9.04 doesnt have the IPv6 option in the menu...

---

### Post by Linuxforall on 2010-01-14
In Jaunty and Karmic, for system wide ipv6 shut off you need to add a line to the kernel parameters.

[http://www.webupd8.org/2009/11/how-to-disable-ipv6-in-ubuntu-910.html](http://www.webupd8.org/2009/11/how-to-disable-ipv6-in-ubuntu-910.html)

---

### Post by chillyomi on 2011-01-08
thank you

---

