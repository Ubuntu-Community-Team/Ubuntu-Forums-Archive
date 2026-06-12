---
title: "Route problem"
date: 2009-03-04
forum: Networking &amp; Wireless
---

### Post by tbrettschneider on 2009-03-04
I am new at Ubuntu Intrepid and I am having problems adding routes to my interfaces.

I tried installing WICD for intrepid but I still cannot add routes. When I am using the commandline:
route add -net 192.168.150.0 netmask 255.255.255.0 gw 10.3.7.8

I get an error :
SIOCADDRT: No such process

Can somebody help me to add some routes that also stay active after a reboot

---

### Post by juan234 on 2009-03-04
see the /etc/network/interfaces file

you want something like this

auto eth0
iface eth0 inet static
address 192.168.168.xxx
netmask 255.255.255.0
gateway 192.168.168.xxx


hope that helps

---

### Post by tbrettschneider on 2009-03-05
> **juan234 said:**
> see the /etc/network/interfaces file

you want something like this

auto eth0
iface eth0 inet static
address 192.168.168.xxx
netmask 255.255.255.0
gateway 192.168.168.xxx


hope that helps

No I am sorry but the situation is that I have to use dhcp in the office, but I must add three route to different subnets through the gateway 10.3.7.8

---

### Post by juan234 on 2009-03-06
I am no expert on networking.  If you need dhcp you can change 

```

auto eth0
iface eth0 inet dhcp
address 192.168.168.xxx
netmask 255.255.255.0
gateway 10.3.7.8

```

> 
I tried installing WICD for intrepid but I still cannot add routes. When I am using the commandline:
route add -net 192.168.150.0 netmask 255.255.255.0 gw 10.3.7.8


it appears that that you are missing the device ie:
 
route add -net 192.56.76.0 netmask 255.255.255.0 dev eth0
adds a route to the network 192.56.76.x via "eth0". The Class C netmask modifier is not really necessary here because 192.* is a Class C IP address. The word "dev" can be omitted here.

see this link [http://linux.about.com/od/commands/l/blcmdl8_route.htm]("http://linux.about.com/od/commands/l/blcmdl8_route.htm")

I have never had to deal with a gw on a different network.

---

### Post by tbrettschneider on 2009-03-06
> **juan234 said:**
> I am no expert on networking.  If you need dhcp you can change 

```

auto eth0
iface eth0 inet dhcp
address 192.168.168.xxx
netmask 255.255.255.0
gateway 10.3.7.8

```



it appears that that you are missing the device ie:
 
route add -net 192.56.76.0 netmask 255.255.255.0 dev eth0
adds a route to the network 192.56.76.x via "eth0". The Class C netmask modifier is not really necessary here because 192.* is a Class C IP address. The word "dev" can be omitted here.

see this link [http://linux.about.com/od/commands/l/blcmdl8_route.htm]("http://linux.about.com/od/commands/l/blcmdl8_route.htm")

I have never had to deal with a gw on a different network.
root@WKS0422:/etc/network# route add -net 192.168.160.0 netmask 255.255.255.0 gw 10.3.7.8 dev eth0
SIOCADDRT: No such process


I tried it with the device, and with the code in interfaces, but still no route shows

---

