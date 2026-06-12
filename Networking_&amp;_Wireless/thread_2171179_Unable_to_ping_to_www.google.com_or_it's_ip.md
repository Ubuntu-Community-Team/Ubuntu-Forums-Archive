---
title: "Unable to ping to www.google.com or it's ip"
date: 2013-08-29
forum: Networking &amp; Wireless
---

### Post by ndnd on 2013-08-29
Hi,
I am fairly new to linux so detailed commands would be helpful. I am running 12.0.4 LTs ubunut server. I recently installed this O.s and it seems to be working fine. However when I checked today I can SSH to the system from inside the network as well as when I am outside the network (I ssh to the router's IP address which forwards the port - thereby simulating how a user from outside can access the system). Now the problem is 


> $ ping 64.233.160.0
PING 64.233.160.0 (64.233.160.0) 56(84) bytes of data.
^C
--- 64.233.160.0 ping statistics ---
4 packets transmitted, 0 received, 100% packet loss, time 3022ms



I am posting my interface file below for reference

> # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
#iface eth0 inet dhcp
iface eth0 inet static
address 192.168.1.30
gateway 192.168.1.1
broadcast 192.168.1.255
netmask 255.255.255.0


Can anyone please guide me as to what is going on.  I do believe users are able to login to the system only that I can't ping sites so I can't use wget to install any other packages.

Thanks in advance.

---

### Post by steeldriver on 2013-08-29
I don't think 64.233.160.0 is pingable - try 8.8.8.8 or 8.8.4.4 (which are google's public DNS servers)

You probably can't ping by name because you don't have any nameservers defined in your interfaces file - try adding

```
dns-nameservers a.b.c.d p.q.r.s
```

at the bottom of your eth0 stanza, where a.b.c.d and p.q.r.s are your chosen primary and secondary DNS servers (if you don't have or don't want to use ISP recommended ones you can use 8.8.8.8 and 8.8.4.4). Or if your router acts as a forwarding DNS server you may just want to use that.

---

### Post by ndnd on 2013-08-29
Hi Steeldrive,
Thanks again. It worked beautifully.

---

