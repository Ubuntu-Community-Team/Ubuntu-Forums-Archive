---
title: "2 interfaces... wrong uses"
date: 2011-09-26
forum: Networking &amp; Wireless
---

### Post by gh0stpirate on 2011-09-26
Hello everyone, i really need my hand held with this as im having extreme issues. I have 2 interfaces, one wireless, one wired. Wired has NO internet, and is ran to a router so i can share some media to my PS3 via wired. My internet comes from my wireless, however, when both are enabled, i have NO internet, as it keeps trying to use my wired connection for internet access, and mediatomb binds to wireless. Fail. When one or the other are disabled, works fine. EX// wireless=off  mediatomb/streaming A.okay.
     wired=off     internet access works, no mediatomb/streaming.
     both=on       complete mess.
im on ubuntu 11.04

wired=eth0

wireless=eth1

i have NO idea how to "route" in network manager and its beyond me, however a simple type:blah blah, check box, blah blah would work.

also, for what its worth, my mediatomb is executed by init.d (service) NOT the normal way (for those that notice mediatomb executable CAN be bound to interface using switches, but the service cannot.)
ps. ive scoured the /etc/mediatomb. working as intended, no option for interface binding, not that it would help cause i have no internet when both interfaces are enabled!

---

### Post by gh0stpirate on 2011-09-27
bump

---

### Post by mebunto on 2011-09-27
Don't know if this helps.  Mediatomb config.xml in /etc/mediatomb/config.xml should has the option to choose the interface:

```
<?xml version="1.0" encoding="UTF-8"?>
<config version="1" xmlns="http://mediatomb.cc/config/1" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://mediatomb.cc/config/1 http://mediatomb.cc/config/1.xsd">
  <server>
    <port>49152</port>
    [COLOR="Red"]<interface>eth0</interface>[/COLOR]
    <name>MediaTomb</name>
    <udn>uuid:ce151e04-a113-4734-9827-ac9653b7d778</udn>
    <home>/var/lib/mediatomb</home>

```
my /etc/network/interfaces looks like this:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
#
# The secondary network interface
#
auto eth1
iface eth1 inet static
address 192.168.2.81
netmask 255.255.255.0
broadcast 192.168.2.255


```

where eth1 is my interface to my iscsi device with the media files and eth0 is my interface to the Internet - so my other devices talk to mediatomb on eth0 and only my Linux machine talks to eth1.

---

