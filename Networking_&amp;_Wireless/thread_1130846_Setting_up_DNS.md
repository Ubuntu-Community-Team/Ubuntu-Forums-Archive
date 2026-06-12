---
title: "Setting up DNS"
date: 2009-04-20
forum: Networking &amp; Wireless
---

### Post by aragilar on 2009-04-20
I'm trying to network two Ubuntu computers so that I can use the host/domain name of one to ssh on another. The router model for my network is RTA1025W.

---

### Post by netztier on 2009-04-20
> **aragilar said:**
> I'm trying to network two Ubuntu computers so that I can use the host/domain name of one to ssh on another. The router model for my network is RTA1025W.

Running DNS might be a bit overkill for just two machines - unless it's for the effort of education, of course. In that case, you might want to start reading here: [Ubuntu Server Guide, 7. Domain Name Service (DNS)]("https://help.ubuntu.com/8.10/serverguide/C/dns.html") 


There are two simpler solutions - which can even coexist:

[SIZE="4"]a) using Zeroconf's mDNS feature with .local[/SIZE]

Provided that both systems run [Zeroconf]("https://help.ubuntu.com/community/HowToZeroconf") (which Ubuntu Desktop generally does with a software called **avahi**), you can always reach the neighboring system with **hostname.local**, so you should always be able to log in remotely like this:

```
user@computer1:~$ ssh computer2.local
```

Using .local should work with all applications, such as ping, ssh, ftp, even mounting a samba share or accessing a web page. It is even compatible with Apple's Zeroconf implementation called "bonjour", so if you have an Apple computer in your LAN running MacOS X, you can reach it via it's hostname and the .local extension:

```
user@computer1:~$ ping powerbook.local
```
[SIZE="1"](assuming that the Apple has "powerbook" configured as it's hostname, of course)
[/SIZE]


[SIZE="4"]b) keeping /etc/hosts in sync across all computers[/SIZE]

[LIST]
[*]for each computer, configure a "static DHCP lease" or a "DHCP reservation" on your router, so each of them always get their own IP address.
[*]add entries to /etc/hosts on *all* systems like shown below
[/LIST]
```
user@host:~$ more /etc/hosts
127.0.0.1       localhost
192.168.0.11    computer1.mydomain.priv        computer1
192.168.0.12    computer2.mydomain.priv        computer2
192.168.0.13    computer3.mydomain.priv        computer2

```

Of course, you will need to replace 192.168.0.10 with values that match what is configured in the DHCP feature of your router, and use the actual host names instead of "computer1" and "computer2".

A suggestion for the domain name: although it might seem an obvious choice, picking **.local** as domain name is **not recommended**, because it can an will generate interoperability problems with avahi: [http://avahi.org/wiki/AvahiAndUnicastDotLocal](http://avahi.org/wiki/AvahiAndUnicastDotLocal) ; if avahi detects that .local is in use, there are cases where it will instantly disable itself. Therefore, you should pick a completely different domain name that should not conflict with any domain names used on the internet.


regards

Marc

---

