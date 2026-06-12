---
title: "can't keep static ip in 10.04"
date: 2010-04-09
forum: Networking &amp; Wireless
---

### Post by confusedstingray on 2010-04-09
I have a dell inspirion 6400/1505 laptop running ubuntu 10.04
has 2 network controllers wired and wireless
the wired is a
  Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
the wireless is a
Intel Corporation PRO/Wireless 3945ABG
I have the wired configured for static ip 192.168.0.105

the wireless through network manager configured
static ip 192.168.0.101
static works great,
reboot and all is lost for the wireless default back to DHCP (wired stays static) and i loose the nameserver and have to reconfigure it all over.
is there away to remove network manager 
an manually edit the wireless settings? 
i know how to edit the wired network interfaces 
do i just add wlan0 as a static ip ? 
any help or direction would greatly appreciated,

---

### Post by Loosewheel on 2010-04-09
Hi confusedstingray

NetworkManager will not manage any interface listed in the '/etc/network/interfaces' file. 
Checkout the man page, type 'man interfaces' in a terminal.
And here's a link that may be useful:
[http://www.debian.org/doc/manuals/reference/ch05.en.html#_the_basic_network_configuration_with_ifupdown](http://www.debian.org/doc/manuals/reference/ch05.en.html#_the_basic_network_configuration_with_ifupdown)

---

### Post by Iowan on 2010-04-11
Having two interfaces in the same subnet violates some standard I can't specify at the moment. Dunno if that's why your configuration won't stick...

---

### Post by confusedstingray on 2010-04-15
> **Iowan said:**
> Having two interfaces in the same subnet violates some standard I can't specify at the moment. Dunno if that's why your configuration won't stick...

i thought as long as only 1 is active it didn't matter

---

