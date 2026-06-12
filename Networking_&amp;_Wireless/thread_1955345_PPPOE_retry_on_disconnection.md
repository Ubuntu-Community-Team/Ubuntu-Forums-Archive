---
title: "PPPOE retry on disconnection"
date: 2012-04-09
forum: Networking &amp; Wireless
---

### Post by numb555 on 2012-04-09
Running Ubuntu Server 10.4, would like to know how to make pppoefconf retry the connection whenever there's a disconnect.

when a disconnect occurs, I always have to manually run 'pon dsl-provider', to re-establish the connection for PPPOE.

anyone know where i can set the variable to retry on disconnection??

Thanks in advance.

---

### Post by praseodym on 2012-04-09
Please show

> cat /etc/network/interfaces
cat /etc/resolv.conf
You want to use dhcp or a static IP?

---

### Post by numb555 on 2012-04-09
/etc/network/interfaces
> 
auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider

auto eth0
iface eth0 inet manual




The PPPoE connection attains a static IP from the ISP ditto for the DNS (resolve.con).

---

### Post by praseodym on 2012-04-09
Change the last line to:
```

iface eth0 inet static
    address 192.168.0.97   # your static IP
    netmask 255.255.255.0  # Netmask
    gateway 192.168.0.1    # Standard-Gateway
```
Does it lack
```
auto lo
iface lo inet loopback
```
?

---

### Post by numb555 on 2012-04-23
solution: for those with similar question about pppoe re-connection.

[http://www.khattam.info/howto-auto-re-connect-to-dsl-pppoe-in-linux-2010-03-07.html](http://www.khattam.info/howto-auto-re-connect-to-dsl-pppoe-in-linux-2010-03-07.html)

add this in your dsl-provider conf file:

persist
maxfail 0
holdoff 10
lcp-echo-interval 20
lcp-echo-failure 3

---

