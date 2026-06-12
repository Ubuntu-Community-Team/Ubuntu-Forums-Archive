---
title: "CAn ping outside but not inside the network"
date: 2009-01-18
forum: Networking &amp; Wireless
---

### Post by ndnd on 2009-01-18
Hi,
I have recently installed 8.10 and the installation went fine. I also have ssh package installed. I am still setting it up. So for now I have simply connected via ethernet cable from the router

I am able to ping google.com however, I can't ping computers inside my network
I can't even ping the router

I have one more laptop on which I had installed the same system - I can ping (internally, to the router and google),ssh without any problems

I am not clear where the problem is. 
I also tried to configure the interfaces file as static settings
 
> 
#iface eth0 inet static
#       address 192.168.1.XXX
#       netmask 255.255.255.0
#       network 192.168.1.0
#       broadcast 192.168.1.255
#       gateway 192.168.1.1
#       # dns-* options are implemented by the resolvconf package, if installed
#       dns-nameservers 192.168.1.1


Any ideas and thoughts would be helpful

Thanks in advance

---

### Post by Iowan on 2009-01-19
> **ndnd said:**
>  ...I can't ping computers inside my network
I can't even ping the router... Ping by name or IP address?

---

### Post by bapoumba on 2009-01-19
Moved to networking.

---

### Post by aaron.d on 2009-01-19
please share:

```
$sudo /sbin/ifconfig
```

```
$cat /etc/resolv.conf
```

```
$traceroute www.google.com
```

```
$sudo /sbin/route -n
```

---

