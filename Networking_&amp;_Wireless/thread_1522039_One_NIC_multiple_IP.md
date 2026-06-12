---
title: "One NIC multiple IP"
date: 2010-07-01
forum: Networking &amp; Wireless
---

### Post by nl2ttl on 2010-07-01
I need the following:

Running XAMMP on Ubuntu server with one NIC.
Only the webserver has to be available on multiple IP addresses.

What i have is 4 devices who communicate with server database servers.

Device 1 = Mysql on IP 192.168.0.100
Device 2 = Mysql on IP 192.168.0.101
Device 3 = Mysql on IP 192.168.0.102
Device 4 = Mysql on IP 192.168.0.103

What i like to do is installing one server and let all the devices communicate with this single database.

Its not posible to change the the devices. So I can not tell them to send data to one IP.

Is something like this possible?

---

### Post by capscrew on 2010-07-01
> **nl2ttl said:**
> I need the following:

Running XAMMP on Ubuntu server with one NIC.
Only the webserver has to be available on multiple IP addresses.

What i have is 4 devices who communicate with server database servers.

Device 1 = Mysql on IP 192.168.0.100
Device 2 = Mysql on IP 192.168.0.101
Device 3 = Mysql on IP 192.168.0.102
Device 4 = Mysql on IP 192.168.0.103

What i like to do is installing one server and let all the devices communicate with this single database.

Its not posible to change the the devices. So I can not tell them to send data to one IP.

Is something like this possible?

Absolutely.  See [**_here_**]("http://www.ubuntugeek.com/ubuntu-networking-configuration-using-command-line.html").  Refer to the section: **Setting up Second IP address or Virtual IP address in Ubuntu**.

---

