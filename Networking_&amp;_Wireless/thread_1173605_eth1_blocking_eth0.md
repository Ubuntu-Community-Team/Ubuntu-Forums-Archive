---
title: "eth1 blocking eth0?"
date: 2009-05-29
forum: Networking &amp; Wireless
---

### Post by LepeKaname on 2009-05-29
I have this configuration in my /etc/network/interfaces:

(*** covering real numbers)
```
auto lo
iface lo inet loopback

# Internet IP
auto eth0
iface eth0 inet static
address 211.***.179.197
netmask 255.255.255.248
gateway 211.***.179.193
dns-nameservers 203.***.160.75
broadcast 211.***.179.199

# Intranet IP
#auto eth1
#iface eth1 inet static
#address 192.168.0.151
#netmask 255.255.255.0
#gateway 192.168.0.254
#dns-nameservers 192.168.0.254
#network 192.168.0.0
#broadcast 192.168.0.255

```

If I uncomment eth1 (and restart networking), I can not ping eth0 anymore from outside. However, from inside the network I can ping both. 

My firewall is disabled, my resolv.conf is empty. Any idea why is this happening?

Thank you.

---

### Post by latev on 2009-05-30
what's your default gateway?
/post the output of the 'route' command/

---

### Post by Adina on 2009-05-30
> **LepeKaname said:**
> 


If I uncomment eth1 (and restart networking), I can not ping eth0 anymore from outside. However, from inside the network I can ping both. 

My firewall is disabled, my resolv.conf is empty. Any idea why is this happening?

Thank you.


When you say ping eth0 from outside, do you mean ping eth0 from internet or from eth1? I don't think you can ping your lan from internet. If you can't ping eth0 from eth1 maybe some problem with your Nat rule or something.

---

### Post by superprash2003 on 2009-05-30
post output of route -n with  and without eth1

---

### Post by LepeKaname on 2009-05-30
$ route -n

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
211.***.179.192 0.0.0.0         255.255.255.248 U     0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         211.***.179.193 0.0.0.0         UG    100    0        0 eth0
0.0.0.0         192.168.0.254   0.0.0.0         UG    100    0        0 eth1
```

$ route
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
211.***.179.192 *               255.255.255.248 U     0      0        0 eth0
192.168.0.0     *               255.255.255.0   U     0      0        0 eth1
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         211.***.179.193 0.0.0.0         UG    100    0        0 eth0
default         192.168.0.254   0.0.0.0         UG    100    0        0 eth1

```

> 
When you say ping eth0 from outside, do you mean ping eth0 from internet or from eth1? 

eth0 is the network card that has the Internet IP, so, by outside I mean from internet.

---

### Post by Adina on 2009-05-30
sorry I got eth0 and eth1 mixed up. Couldn't you get dhcp from your isp on eth0? or maybe just try that first and then change it to static after you get it all to work.

---

### Post by Chris_no on 2009-05-30
Why have you made eth0 broadcast on 211.***.179.199 and not 211.***.179.255?

Never mind my question! Found my answer here: 
[http://www.linuxquestions.org/questions/linux-newbie-8/what-is-a-broadcast-ip-42900/](http://www.linuxquestions.org/questions/linux-newbie-8/what-is-a-broadcast-ip-42900/)

---

### Post by latev on 2009-05-30
I think your problem is the two default gateways that you have!
Try to get rid of
default         192.168.0.254   0.0.0.0         UG    100    0        0 eth1
and see if it works
/the easiest way I think would be to comment the line out in your interfaces file/

> When you say ping eth0 from outside, do you mean ping eth0 from internet or from eth1? I don't think you can ping your lan from internet. If you can't ping eth0 from eth1 maybe some problem with your Nat rule or something.

1) Yes, you can ping the machine from anywhere on any interface through any interface /or should be able to/
2) In order to ping eth0 from eth1 you should have forwarding enabled
echo 1 > /proc/sys/net/ipv4/ip_forward

---

### Post by redmk2 on 2009-05-30
> **Chris_no said:**
> Why have you made eth0 broadcast on 211.***.179.199 and not 211.***.179.255?

The OP is using a network with only 6 usable IP addresses in it plus the network and b'cast addresses, for a total of 8 addresses.  See the subnet mask of 255.255.255.248?  this means that we only  have 3 bits of addressing space.  

The network address is 211.***.179.192 and the b'cast is 199.  The next network is .200 and the b'cast of that is .215 and so on.  The last network in this range is 211.***.179.248 to 211.***.179.255

---

### Post by Chris_no on 2009-05-30
It took me a little while to process that...

Had to switch to binary mode. ;)

---

### Post by LepeKaname on 2009-05-31
[QUOTE=latev;7372803]I think your problem is the two default gateways that you have!
Try to get rid of
default         192.168.0.254   0.0.0.0         UG    100    0        0 eth1
and see if it works
/the easiest way I think would be to comment the line out in your interfaces file/

It worked!! Thank you very much!! I didn't thought about that... 

Thank you everyone for your time.

---

