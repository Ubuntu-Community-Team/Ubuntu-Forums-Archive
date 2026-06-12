---
title: "Forcing DNS IP address"
date: 2009-06-02
forum: Networking &amp; Wireless
---

### Post by austinium on 2009-06-02
Iam using Ubuntu 9.04, via Wubi. On Windows i have forced DNS IP addresses and the internet connection works fine. I tried the same DNS IP addresses on ubuntu by adding them to /etc/resolv.conf wrote nameserver IP_ADDRESS

its not working, iam connecting through a router and iam able to ping the router's local IP address, iam also able to ping the DNS IP address.


help!

---

### Post by Iowan on 2009-06-02
Is your address DHCP or static? Perhaps you've already used the "prepend" line in /etc/dhcp3/dhclient.conf?

---

### Post by austinium on 2009-06-03
i have one of those DSL Routers, so the IP address is DHCP and iam trying to statically assign(force) DNS IP addresses on Ubuntu, this setup works in WindowsXP(Forced DNS).

How do i fix this?

thanks

---

### Post by superprash2003 on 2009-06-03
opendns servers forced in this example [http://www.prash-babu.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://www.prash-babu.com/2008/04/how-to-configure-dns-servers-in-linux.html)

---

### Post by austinium on 2009-06-07
that didn't work, any other ideas?

---

### Post by PatrickVogeli on 2009-06-07
If you are using network manager, just right click on the applet and select "Edit conections". There choose wired or wireless and edit the one you need (probably eth0 for wired, and auto network-name for wireless). The click edit and on IPV4 parameters only addreces automatically or something like that.

There you'll be able to enter new DNS

---

