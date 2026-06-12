---
title: "Networking wont start after a reboot"
date: 2009-03-28
forum: Networking &amp; Wireless
---

### Post by wabbit46 on 2009-03-28
I am running ubuntu 8.04 LTS. 

Every time I reboot my ubuntu machine it refuses to connect to the network.

Typing in a terminal session sudo /etc/init.d/ networking stop comes back with the message "RTNETLINK answers: No such process"

If I then enter sudo /etc/init.d networking start all is back to normal.

What do I need to do to make networking come up automatically on reboot ?

---

### Post by superprash2003 on 2009-03-28
post output of **cat /etc/network/interfaces** from your terminal

---

### Post by wabbit46 on 2009-03-28
> **superprash2003 said:**
> post output of **cat /etc/network/interfaces** from your terminal

The contents of this are displayed below :-

auto lo
iface lo inet loopback


iface eth0 inet static
address 192.168.0.210
netmask 255.255.255.0
gateway 192.168.0.1

auto eth0


iface eth1 inet static
address 192.168.0.202
netmask 255.255.255.0
gateway 192.168.0.1

auto eth1

---

### Post by superprash2003 on 2009-04-01
why do you have two interfaces pointing to the same gateway?

---

### Post by wabbit46 on 2009-04-02
> **superprash2003 said:**
> why do you have two interfaces pointing to the same gateway?

I set the second NIC up after I thought the first may be faulty. I have changed the gateway address of the second to 192.168.0.50 but I still have no network available after a reboot.

---

### Post by wabbit46 on 2009-04-02
I removed the second NIC but still had no success.

I manually deleted all references to it in the /etc/network/interfaces file and all works properly again.

Thanks for pointing me in the right direction.

---

