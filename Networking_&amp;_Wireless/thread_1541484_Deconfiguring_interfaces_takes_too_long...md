---
title: "Deconfiguring interfaces takes too long.."
date: 2010-07-29
forum: Networking &amp; Wireless
---

### Post by BugBuster on 2010-07-29
Hi, I have added a second ethernet card to my desktop and since then I have a strange problem. Whenever I have some entry in /etc/resolv.conf,  restarting networking service takes very long like 10-20 seconds whereas earlier it happend in a flash. Also while shutdown it pauses at 'Deconfiguring interfaces'..As a result it now takes 20 secs to shutdown while earlier it took only 5-8 secs.

Here is my /etc/network/interfaces file;

```

## Loopback
auto lo
iface lo inet loopback

## Ethernet(Gateway to Internet)
auto eth0
iface eth0 inet static
address 192.168.1.10
netmask 255.255.255.0

## Ethernet (Local Services)
auto eth1
iface eth1 inet static
address 192.168.0.10
netmask 255.255.255.0

```

What could be the reason.
Everything works fine if I remove the resolv.conf file or when it is empty.

---

### Post by Iowan on 2010-07-30
> **BugBuster said:**
> Everything works fine if I remove the resolv.conf file or when it is empty. What's in */etc/resolv.conf*?

---

### Post by BugBuster on 2010-07-30
> **Iowan said:**
> What's in */etc/resolv.conf*?

```

nameserver 208.67.222.222
nameserver 208.67.220.220

```

---

