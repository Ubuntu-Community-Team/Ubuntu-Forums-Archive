---
title: "using desktop-pc as gateway"
date: 2010-07-22
forum: Networking &amp; Wireless
---

### Post by jigneshvasoya on 2010-07-22
i want to use pc as gateway..
i have pc with ubuntu 10.04 with 2NICS..
eth1(ip is 10.6.15.254) - NIC1 is connected to local network 10.6.15.0
eth2(ip is 10.6.0.115) -NIC2 is connected to the external world(internet)

From any client machine within the 10.6.15.0 network i m able to access the other machine in 10.6.15.0 network..
But i can not access the machine outside the 10.6.15.0 network
From client machine i can ping the 10.6.15.254 and 10.6.0.115 but not out side world
But from gateway(10.6.15.254) i am able to access the internet...
Local machine are not able to ping the external world(internet)

---

### Post by Iowan on 2010-07-22
[This]("https://help.ubuntu.com/community/Internet/ConnectionSharing") may not solve all the problems, but should be a good place to start...

---

### Post by YesWeCan on 2010-07-22
> **jigneshvasoya said:**
> i want to use pc as gateway..
i have pc with ubuntu 10.04 with 2NICS..
eth1(ip is 10.6.15.254) - NIC1 is connected to local network 10.6.15.0
eth2(ip is 10.6.0.115) -NIC2 is connected to the external world(internet)

From any client machine within the 10.6.15.0 network i m able to access the other machine in 10.6.15.0 network..
But i can not access the machine outside the 10.6.15.0 network
From client machine i can ping the 10.6.15.254 and 10.6.0.115 but not out side world
But from gateway(10.6.15.254) i am able to access the internet...
Local machine are not able to ping the external world(internet)

You need to make your PC act like a router.
Any packets it receives from eth1 need to be routed to the eth2 gateway and the replies routed back again. This can be done using the iptables masquerade directive.

If you do not have any iptables directives set up (which is the default after a new install of Ubuntu) then all you need to do is:
```

sudo -s
echo 1 > /proc/sys/net/ipv4/ip_forward
exit

sudo iptables -t nat -A POSTROUTING -s 10.6.15.0/24 -o eth2 -j MASQUERADE
```
Note that these setting will be lost on reboot; Google for how to make them permanent.
Your eth1 clients need to have 10.6.15.254 as their default gw.
Then you may want to add a dhcp service so your eth1 clients can get told the DNS server addresses and be assigned IP addresses automatically. See: [http://www.linuxtopia.org/online_books/system_administration_books/ubuntu_starter_guide/ch07s04.html](http://www.linuxtopia.org/online_books/system_administration_books/ubuntu_starter_guide/ch07s04.html)

---

