---
title: "Wired internet connection doesn't work, after using wireless connection"
date: 2009-05-14
forum: Networking &amp; Wireless
---

### Post by SteveF48 on 2009-05-14
I took my Sony laptop to my brother's place and used his wireless internet connection. I now have my laptop back and cannot connect to the Internet.
I can happily browse my home network and view files on my Windoze PCs (and vice versa);
I can ping IP addresses, but not sites by name. 
Network manager says 'No active connections found'.
I have an ethernet connection to a Netgear DG834 router, which has its own ADSL modem built-in.
I'm using version 8.04 of Ubuntu.

---

### Post by superprash2003 on 2009-05-14
post output of **ifconfig** from the terminal

---

### Post by bluestreek on 2009-05-14
Make sure all your DCHP settings are correct. Perhaps you need to change them to connect to that wireless?

---

### Post by Iowan on 2009-05-14
> **SteveF48 said:**
> 
I can ping IP addresses, but not sites by name.  Check */etc/resolv.conf* for proper DNS servers and search domain.

---

