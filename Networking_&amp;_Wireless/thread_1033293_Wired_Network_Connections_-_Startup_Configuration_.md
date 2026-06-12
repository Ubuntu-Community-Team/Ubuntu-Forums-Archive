---
title: "Wired Network Connections - Startup Configuration Default"
date: 2009-01-07
forum: Networking &amp; Wireless
---

### Post by helstreak on 2009-01-07
I guess there is 2 types of network connections and 1 that actually works.  The one that is configured to start when I start the comp doesn't work so I have to tell it which one to use.  How do I set the default?

The names of the 2 connections are:
Davicom Semiconductor, Inc. 21x4x DEC-Tulip compatible 10/100 Ethernet
National Semiconductor Corporation DP83820 10/100/1000 Ethernet Controller

The one that lets me connect to the internet is the Davicom connection.

How do I set the Davicom connection as the default?

I'm using Ubuntu 8.04

Thanks for the help :)

---

### Post by Iowan on 2009-01-07
Post results of **ifconfig -a**, and results of **lspci**.

---

### Post by helstreak on 2009-01-07
> **Iowan said:**
> Post results of **ifconfig -a**, and results of **lspci**.

What is the purpose of each result?  Just wondering...

---

### Post by Iowan on 2009-01-07
**lspci** will show if system recognizes card (probably unnecessary if it works manually). **ifconfig -a** shows configuration details (IP Address in particular) for all interfaces (not just active ones).  It also shows which interface(s) is(are) configured to activate on bootup (auto line).
** lshw -C network** will show which card is associated with which "eth".
If the "bad" one is set to "auto" and the "good" one is not, the fix *might* be pretty easy - "auto" the good one instead.

---

### Post by helstreak on 2009-01-07
> **Iowan said:**
> **lspci** will show if system recognizes card (probably unnecessary if it works manually). **ifconfig -a** shows configuration details (IP Address in particular) for all interfaces (not just active ones).  It also shows which interface(s) is(are) configured to activate on bootup (auto line).
** lshw -C network** will show which card is associated with which "eth".
If the "bad" one is set to "auto" and the "good" one is not, the fix *might* be pretty easy - "auto" the good one instead.

the "bad" is set to auto...how do I set the "good" to auto?

---

### Post by Iowan on 2009-01-07
If both have entries in /etc/network/interfaces, change the number on the "auto" line (eg. change **auto eth0** to **auto eth1**).  If there is no entry for the "good" one... I'll be confused how it can work, but quick/dirty will be to change the entry (eg. from **iface eth0 inet dhcp** to **iface eth1 inet dhcp**).

---

### Post by helstreak on 2009-01-08
> **Iowan said:**
> If both have entries in /etc/network/interfaces, change the number on the "auto" line (eg. change **auto eth0** to **auto eth1**).  If there is no entry for the "good" one... I'll be confused how it can work, but quick/dirty will be to change the entry (eg. from **iface eth0 inet dhcp** to **iface eth1 inet dhcp**).

not sure what i did but it worked.  i changed the interfaces file

*********************************************************************
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth1
#iface eth1 inet dhcp
**********************************************************************

to

**********************************************************************
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
**********************************************************************

the last 2 lines are what i changed
what did i do lol?

---

### Post by Iowan on 2009-01-08
I gotta guess that eth0 was the "good" one and eth1 was the "bad" one, so what you did was tell the system to start up eth0 instead of eth1. Glad it worked for you.  If it stays fixed, mark the thread as [SOLVED] (Under Thread Tools].

---

### Post by helstreak on 2009-01-09
> **Iowan said:**
> I gotta guess that eth0 was the "good" one and eth1 was the "bad" one, so what you did was tell the system to start up eth0 instead of eth1. Glad it worked for you.  If it stays fixed, mark the thread as [SOLVED] (Under Thread Tools].

In the above code what is the line:
iface eth0 inet dhcp
doing?

---

