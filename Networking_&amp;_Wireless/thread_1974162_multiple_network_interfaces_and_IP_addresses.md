---
title: "multiple network interfaces and IP addresses"
date: 2012-05-05
forum: Networking &amp; Wireless
---

### Post by Cycorp on 2012-05-05
[B][SIZE=2]We have a system that has 4 ethernet ports

Eth0 and Eth2 are connect to a Comcast connection.

Eth0 is connect via a firewall and has an ip of 192.168.0.1 gateway/firewall device is 192.168.0.253

i would like Eth1 to be connected directly to the Comcast SMC modem with an IP of 192.168.253.10 gateway 192.168.0.254.

Eth1 is connected to CBeyond directly with an IP address 192.168.252.1 with an gateway of 192.168.252.254

If Comcast is down I would like to route all traffic on the 192.168.0.x network via the 192.168.252.1/192.168.252.254 as a gateway with a firewall. This change over does not need to be automatic since I will be able to get into the server via CBeyond.

What should I have in interfaces, routes and other files ?

How do I setup an OS firewall on Eth1 and Eth2 or should I use the firewall for all Eth ports ?

When using a web browser how can I tell it which Eth to use ?

Thanks [/SIZE][/B]

[SIZE=3][COLOR=blue]Cycorp[/COLOR][/SIZE]

---

### Post by newbie-user on 2012-05-05
You /etc/network/interfaces file should look like this:

```
auto eth0
iface eth0 inet static
     address 192.168.0.1
     netmask 255.255.255.0
     broadcast 192.168.0.255
     network 192.168.0.0
     gateway 192.168.0.253
     dns-name-servers [your isp dns]

auto eth1
iface eth1 inet static
     address 192.168.253.10
     netmask 255.255.0.0
     broadcast 192.168.255.255
     network 192.168.0.0

auto eth2
iface eth2 inet static
     address 192.168.252.1
     netmask 255.255.255.0
     broadcast 192.168.252.255

up route add default gw 192.168.0.253 dev eth0

```

That takes care of the static ip setup and the web browsing. You should set up a firewall on all your Internet-facing network interfaces

---

