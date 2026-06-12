---
title: "Wubi Install of 8.10 connects to wireless but no other internet access"
date: 2009-02-25
forum: Networking &amp; Wireless
---

### Post by Gordonbp531 on 2009-02-25
I've done the usual - disabled ipv6 in Firefox, uncommented the "prepend nameserver" line and added the ISP name servers in /etc/dhcp3/dhclient.conf, commented the original line (alias net-pf-10 ipv6) and added the line (alias net-pf-10 off) both without brackets of course! in the file /etc/modprobe.d/aliases and still no internet access.
What next?

---

### Post by jimmyhacker on 2009-02-25
dude you said your answer yourself.undo your changes (enable ipv6,etc.)and try to acces internet with other things.

---

### Post by Gordonbp531 on 2009-02-26
> **jimmyhacker said:**
> dude you said your answer yourself.undo your changes (enable ipv6,etc.)and try to acces internet with other things.

That's the whole point - it doesn't access with all those enabled. It's always been the same with Ubuntu on my ISP - I've had to do these edits but even these don't work currently.

---

### Post by Gordonbp531 on 2009-02-26
> **gendibal said:**
> That's the whole point - it doesn't access with all those enabled. It's always been the same with Ubuntu on my ISP - I've had to do these edits but even these don't work currently.

In addition - I now have two machines side by side - a Toshiba Netbook with Ubuntu remix on, and the Wubi install of 8.10 on the laptop.
Settings on both are identical AFAICS.
BOTH can see and connect to the wireless network, but only the Netbook can access the internet!

Why is this?

---

### Post by j0rd on 2009-02-26
I have a similar issue since upgrading to 8.10 this morning.

With my laptop under vanila ubuntu 8.10 I am able to connect to my wireless (and wired) connections....but neither of them will allow me to access the internet. Both wired and wireless get IPs via DHCP...but then no internet.

I flushed iptables with iptables -F ... i checked out the routes, gateway and netmask...all look correct...but when I try and ping my gateway (192.168.1.254) I get "ping: sendmsg: Operation not permitted" error. Same thing if I ping as root.

If I ping yahoo.com i get host not known. I've played around with my resolv.conf and also tried to ping other IPs directly, to no avail.

I knew upgrading was a bad idea for a productive day :D

---

