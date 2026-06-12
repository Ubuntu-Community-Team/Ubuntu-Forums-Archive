---
title: "Problems Accessing Internet"
date: 2011-07-01
forum: Networking &amp; Wireless
---

### Post by nslatter on 2011-07-01
I'm having some issues connecting to the internet with my newly installed ubuntu server 11.04.  I can actually access the server from my internal network (I'm able to connect to it via ftp as well as ssh) but when I attempt to nslookup google.com, I get the error

```
;; connection timed out; no server could be reached.
``` 

/etc/network/interfaces

auto eth0
iface eth0 inet static
address 192.168.1.150
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1

/etc/resolve.conf

nameserver 192.168.1.1

I'm just not sure what to attempt next.

Thanks in advance for any help.

---

### Post by collisionystm on 2011-07-01
> **nslatter said:**
> I'm having some issues connecting to the internet with my newly installed ubuntu server 11.04.  I can actually access the server from my internal network (I'm able to connect to it via ftp as well as ssh) but when I attempt to nslookup google.com, I get the error

```
;; connection timed out; no server could be reached.
```/etc/network/interfaces

auto eth0
iface eth0 inet static
address 192.168.1.150
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1

/etc/resolve.conf

nameserver 192.168.1.1

I'm just not sure what to attempt next.

Thanks in advance for any help.

After you set your /etc/network to static, did you restart your networking services?

```
sudo /etc/init.d/networking restart
```

---

### Post by nslatter on 2011-07-01
I did...  a few times actually... :D

Thanks for the reply.

---

### Post by nslatter on 2011-07-01
I ended up reinstalling the OS. This worked so I must have messed something up in the original install.

---

