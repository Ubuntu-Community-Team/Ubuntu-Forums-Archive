---
title: "No outgoing connection (VMware)"
date: 2010-02-16
forum: Networking &amp; Wireless
---

### Post by Rulesy on 2010-02-16
Hi, I'm running Ubuntu 8.04.3 server on my XP Pro SP3 machine using VMWare. I'm trying to set up a static IP address but I can no longer ping anything except my router (not even the XP machine it's hosted on)

I'm using "bridged" mode in VMware

Here's my /etc/network/interfaces file:

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.50
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1

```Any ideas?

Thanks

---

### Post by superprash2003 on 2010-02-17
what is the ip address of the xp machine?you mean your able to ping 192.168.1.1 ?

---

### Post by Rulesy on 2010-02-17
Yes, that's correct. My XP machine is on DHCP, currently using 192.168.1.122.

I've set up a LAMP server and can actually connect ok to it, just cannot connect FROM it :(

---

### Post by Rulesy on 2010-02-17
Any ideas? Don't make me install Zend :(

---

### Post by jschwartz73 on 2010-02-23
Try changing your gateway to 192.168.1.2

I believe 192.168.1.1 is the IP on the host side and 192.168.1.2 is the guest side.

Hope that works.

---

