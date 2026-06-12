---
title: "Problem when configing /etc/network/interfaces"
date: 2009-08-29
forum: Networking &amp; Wireless
---

### Post by carfield on 2009-08-29
When I config eth0 as 
```
iface eth0 inet dhcp
```

It is working , and with ifconfig out put as
```

eth0      Link encap:Ethernet  HWaddr 00:1d:60:35:85:b1  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:60ff:fe35:85b1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3949192 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3719570 errors:0 dropped:0 overruns:0 carrier:8
          collisions:0 txqueuelen:1000 
          RX bytes:3286837504 (3.2 GB)  TX bytes:1986915307 (1.9 GB)

```

However , I in fact would like to hardcode it as 192.168.1.2, thus I try:

```
iface eth0 inet static
            address 192.168.1.2
            gateway 192.168.1.1
            netmask 255.255.255.0

```

Then it show exactly same ifconfig output, but with the internet connection is not working :-( 

Would anyone suggest me what going wrong?

---

### Post by dbalascak on 2009-08-29
The IP of the DNS has to be set, as you are no longer getting DNS info from DHCP.
Two ways. 
edit /etc/resolv.conf
```

nameserver 192.168.1.1

```

or 

add it to **/etc/network/interfaces**
```

auto eth0
iface eth0 inet static
address 192.168.1.2
netmask 255.255.255.0
gateway 192.168.1.1
dns-nameservers 192.168.1.1


```

---

### Post by carfield on 2009-08-30
Great, that work!

---

