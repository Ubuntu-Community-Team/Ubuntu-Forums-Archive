---
title: "Making Xubuntu a Gateway"
date: 2009-01-19
forum: Networking &amp; Wireless
---

### Post by Arukas on 2009-01-19
Does anyone know any good tutorials on how to make a gateway out of Xubuntu.  I would like to do more with it, but I want to start with the simple things.


I have read pages at aboutdebian, bit-tech, cyberdogtech, and a ubuntu page about gatways.  The debian site seem to just "talk about it" but leaves the details out.  And the other rest just don't give me enough information, because in the end the scripts don't work right, because they don't tell how to use them.  

I would appreicate some help.

---

### Post by bgerlich on 2009-01-19
Basically, if you mean a router (gateway):

1. Turn on Ip forwarding:
```
sudo sysctl -w net.ipv4.ip_forward=1
```
2. Turn on IP Masquerade (NAT) xxx? - this is the interface connecting with the internet (eth0, ppp0, ...):
```
sudo iptables -t nat -A POSTROUTING -o xxx? -j MASQUERADE
```
3. Install dhcp server:
```
sudo apt-get install dhcp3-server
```
4. Setup internal card's ip address to some static address.
5. Configure it, of course, example config file below, remember to change your config to fit your internal network and internal card's IP.
Example /etc/dhcp3/dhcpd.conf:
```
option domain-name-servers 4.2.2.1, 4.2.2.2;

default-lease-time 600;
max-lease-time 7200;

log-facility local7;

subnet 10.0.1.0 netmask 255.255.255.0 {
  range 10.0.1.10 10.0.1.20;
  option routers 10.0.1.1;
}
```

Remember to restart the server afterwards by sudo /etc/init.d/dhcp3-server restart

The Ip forwarding setting will not last through the restart, you can enable the Ip forwarding permanently in /etc/sysctl.conf.

---

### Post by Arukas on 2009-01-19
I don't want my gateway to assign IP address, I want them to be static, How do I do that?

---

### Post by Arukas on 2009-01-19
Doesn't dhcp give out random IP address?  What the point of it, when I have static IPs?

---

### Post by Arukas on 2009-01-19
Okay I read through you little info, and its no where near complete it leaves out a lot of stuff that assume I know, I know some of it, but not all of it.

I need a good guide on how to setup Xubuntu as a gateway.

---

### Post by Arukas on 2009-01-20
Someone has to know of some good guides how to turn ubuntu into a gateway.  I've made scripts and run but they don't make the gateway work.

---

