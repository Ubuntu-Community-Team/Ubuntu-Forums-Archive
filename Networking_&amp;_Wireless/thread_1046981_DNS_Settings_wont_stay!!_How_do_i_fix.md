---
title: "DNS Settings wont stay!! How do i fix?"
date: 2009-01-21
forum: Networking &amp; Wireless
---

### Post by Spoken on 2009-01-21
Every time i boot up i have to go to my network options and change my DNS settings.  Esentially, after bootup, my router address and my ip address are in the reverse order they should be.  which makes my internet super slow.  when i change them, its fast, but it wont save,  every time i reboot i have to repeat this process.  how to i make the dns config stay?

---

### Post by x33a on 2009-01-22
try entering dns servers directly to

/etc/resolv.conf

---

### Post by superprash2003 on 2009-01-22
resolv.conf is usually overwritten by your router. you could enter it in the dhclient.conf file.. [http://www.prash-babu.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://www.prash-babu.com/2008/04/how-to-configure-dns-servers-in-linux.html)

---

### Post by Iowan on 2009-01-22
_IF_ you get a DHCP address, the "prepend domain-name-servers" line in /etc/dhcp3/dhclient.conf should make it stick.

In hindsight - most of the details are in **superprash2003**'s link...

---

