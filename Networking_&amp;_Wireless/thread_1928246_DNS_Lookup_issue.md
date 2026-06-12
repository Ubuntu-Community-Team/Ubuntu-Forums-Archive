---
title: "DNS Lookup issue?"
date: 2012-02-19
forum: Networking &amp; Wireless
---

### Post by Bytesunfish on 2012-02-19
My server which has been running for quite some time has been having some troubles. I first noticed this when I was doing updates and got the "something wicked has happened" message

```
Err http://security.ubuntu.com natty-security Release.gpg
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
```

and pinging known reliable servers is not functioning.

```
***@***:~$ping www.google.com
ping: unknown host www.google.com
```

My interfaces file:
```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
```
My hosts file:
```
127.0.0.1       localhost
127.0.1.1       m2neubuntu

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
```
Printout of route -n
```
****@****:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.1.2     0.0.0.0         UG    100    0        0 eth0
```
Contents of /etc/resolv.conf
```
nameserver 192.168.1.1
```

other pertinent information:
-Server gets Static IP from DD-WRT router
-Can connect to it remotely
-Can ping addresses when using actual ip addresses
-Swapped routers recently. New router has a different IP
-Version 11.04 64-bit (server)

Mayor Bytesunfish

---

### Post by Iowan on 2012-02-19
Also include results of **route -n**,and contents of */etc/resolv.conf*.

---

### Post by Bytesunfish on 2012-02-19
After seeing that my resolv.conf did not match the router's ip address I changed that and I was golden. Thanks for the quick reply!

Mayor Bytesunfish

---

### Post by Iowan on 2012-02-19
EXCELLENT! It's nice to win one occasionally.

---

