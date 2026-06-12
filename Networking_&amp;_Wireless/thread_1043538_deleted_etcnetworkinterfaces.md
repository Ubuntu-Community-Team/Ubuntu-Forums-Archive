---
title: "deleted /etc/network/interfaces"
date: 2009-01-18
forum: Networking &amp; Wireless
---

### Post by stmartin on 2009-01-18
Hello!

I suddenly delted /etc/network/interfaces. How to recover it? 

Thanks in advance.

Regards.

---

### Post by linuxuser21 on 2009-01-18
Try this: [http://www.stellarinfo.com/linux-data-recovery.htm](http://www.stellarinfo.com/linux-data-recovery.htm).  It's a trial though.  I haven't got a chance to try the Linux version out, so I don't know well it will work.

---

### Post by Sprut1 on 2009-01-18
Would it be hard to reproduce? :)

My interface file is stripped down to "lo" only:)

---

### Post by stefangr1 on 2009-01-18
No, it is very simple (depending on your specific configuration off caurse).

This is the default:
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

---

### Post by stmartin on 2009-01-18
Thanks for the replies. I am using Broadband connection with DHCP server. Could this somehow interrupt my network or should I leave it deleted?

---

### Post by felker2 on 2009-01-18
> **stefangr1 said:**
> No, it is very simple (depending on your specific configuration off caurse).

This is the default:
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

Mine only has the lo stuff, not the eth0. And my network works :confused:

---

### Post by Sprut1 on 2009-01-18
> **felker2 said:**
> Mine only has the lo stuff, not the eth0. And my network works :confused:

If you use an external network manager that'll set everything up for you.

---

### Post by stmartin on 2009-01-19
I got the Network Manager.

---

