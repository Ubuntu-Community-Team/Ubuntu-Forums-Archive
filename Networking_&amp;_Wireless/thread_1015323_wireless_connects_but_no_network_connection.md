---
title: "wireless connects but no network connection"
date: 2008-12-18
forum: Networking &amp; Wireless
---

### Post by usman.patel on 2008-12-18
Hello,

I have ubuntu 8.10 installed inside Vista using wubi.

My problem is the wireless connection.  It connects to my router and gets an IP address but cannot access the internet or even ping the default gateway (wireless router).  However, it can pick up IP address as DHCP works fine on it.  DHCP offer comes from the wireless router.

I have even disabled the UFW (firewall) as I heard it may be 'quarantining' my WLAN0 interface, but still no joy.

Wired connection works fine.


Thanks in advance.
usman.



-------------------------------
My PC is E-System 1201 laptop.
Wireless card is Realtek RTL8187B

---

### Post by teqnilogik on 2009-01-31
I had a similar problem with my Realtek RTL8187B wireless.  I solved it by installing the Windows 98 driver using ndiswrapper.  I posted a how-to in this thread: [http://ubuntuforums.org/showthread.php?t=1021087](http://ubuntuforums.org/showthread.php?t=1021087)

---

