---
title: "Ethernet connection issue"
date: 2012-07-03
forum: Networking &amp; Wireless
---

### Post by kaustubhg123 on 2012-07-03
Here is my /etc/network/interfaces file:
#The loopback network interface
auto lo
iface lo inet loopback

#The primary network interface
auto eth0
iface eth0 inet static
address 192.168.0.27
netmask 255.255.255.0
gateway 192.168.0.1

auto eth0:1
iface eth0 inet static
address 192.168.0.37
netmask 255.255.255.0
gateway 192.168.0.1

But when I run “/etc/init.d/networking restart” I get following:
*Reconfiguring network interfaces…
/etc/network/interface:16:duplicate interface
ifdown: couldn’t read interfaces file “/etc/network/interfaces”
/etc/network/interfaces:16: duplicate interface
ifup: couldn’t read interfaces file “/etc/network/interfaces” [fail]

---

### Post by redmk2 on 2012-07-03
> **kaustubhg123 said:**
> Here is my /etc/network/interfaces file:
#The loopback network interface
auto lo
iface lo inet loopback

#The primary network interface
auto eth0
iface eth0 inet static
address 192.168.0.27
netmask 255.255.255.0
gateway 192.168.0.1

[COLOR="Red"]**auto eth0:1**[/COLOR]
[COLOR="Blue"]**iface eth0 inet static**[/COLOR]
address 192.168.0.37
netmask 255.255.255.0
gateway 192.168.0.1

But when I run “/etc/init.d/networking restart” I get following:
*Reconfiguring network interfaces…
/etc/network/interface:16:duplicate interface
ifdown: couldn’t read interfaces file “/etc/network/interfaces”
/etc/network/interfaces:16: duplicate interface
ifup: couldn’t read interfaces file “/etc/network/interfaces” [fail]

This only brings up the interface upon boot```

[COLOR="Red"]**auto eth0:1**[/COLOR]
```

This defines the interface```
[COLOR="Blue"]**iface eth0 inet static**[/COLOR]
```
... It should be this```
[COLOR="Green"]**iface eth0:1 inet static**[/COLOR]
```

---

### Post by wildmanne39 on 2012-07-03
Hi, thread moved to it's own thread.

Please do not post in any thread that is a year or more older.
Thanks

---

