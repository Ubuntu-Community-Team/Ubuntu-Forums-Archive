---
title: "ubuntu 8.04.2 NAT do not work"
date: 2009-03-31
forum: Networking &amp; Wireless
---

### Post by kaschei_ on 2009-03-31
Hi to all. I use ubuntu 8.04.2 server (2.6.24-23-server) and I wanna share my internet to the second PC running windows XP. On ubuntu I have 2 lan cards eth0 and ppp0 are my internet devices and eth1 is the lan device. I found a lot information how to do that but nothing did not work at all. Please some one to share his/her experience with me.

---

### Post by bgerlich on 2009-03-31
```
sudo apt-get install dhcp3-server
```

Next, configure your /etc/dpcp3/dhcpd.conf to look something like this:
```
ddns-update-style none;

default-lease-time 600;
max-lease-time 7200;

authoritative;

log-facility local7;

subnet 10.0.1.0 netmask 255.255.255.0 {
  range 10.0.1.10 10.0.1.50;
  option routers 10.0.1.1;
  option domain-name-servers 4.2.2.1;
}
```

and your file /etc/network/interfaces to look somethink like this:
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
      address 10.0.1.1
      netmask 255.255.255.0
      network 10.0.1.0
      broadcast 10.0.1.255
      up iptables -t nat -A POSTROUTING -s 10.0.1.0/24 -o ppp0 -j MASQUERADE

```

next make sure that your ppp0 internet connection is setup properly and that you have Ip Forwarding turned on - you do that in the file /etc/sysctl.conf by setting the option net.ipv4.conf.default.forwarding=0 to "1". Now restart your computer or the networking and everything should work well.

---

### Post by kaschei_ on 2009-04-01
> **bgerlich said:**
> ```
sudo apt-get install dhcp3-server
```

Next, configure your /etc/dpcp3/dhcpd.conf to look something like this:
```
ddns-update-style none;

default-lease-time 600;
max-lease-time 7200;

authoritative;

log-facility local7;

subnet 10.0.1.0 netmask 255.255.255.0 {
  range 10.0.1.10 10.0.1.50;
  option routers 10.0.1.1;
  option domain-name-servers 4.2.2.1;
}
```

and your file /etc/network/interfaces to look somethink like this:
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
      address 10.0.1.1
      netmask 255.255.255.0
      network 10.0.1.0
      broadcast 10.0.1.255
      up iptables -t nat -A POSTROUTING -s 10.0.1.0/24 -o ppp0 -j MASQUERADE

```

next make sure that your ppp0 internet connection is setup properly and that you have Ip Forwarding turned on - you do that in the file /etc/sysctl.conf by setting the option net.ipv4.conf.default.forwarding=0 to "1". Now restart your computer or the networking and everything should work well.

No this not working. This is the how I did the job
1. In first I started my own dns server - dnsmasq
2. NAT
```

iptables -t nat -A POSTROUTING -s 192.168.0.0/255.255.255.0 -o ppp0 -j MASQUERADE
iptables -t mangle -A PREROUTING -i ppp0 -j TTL --ttl-inc 1
iptables -t mangle -A INPUT -i ppp0 -j TTL --ttl-dec 1
iptables -t mangle -A POSTROUTING -o ppp0 -j TTL --ttl-set 64
iptables -A FORWARD -p tcp -m tcp --tcp-flags SYN,RST SYN -j TCPMSS --clamp-mss-to-pmtu

```

---

