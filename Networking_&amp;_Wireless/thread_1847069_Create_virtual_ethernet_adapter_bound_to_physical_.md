---
title: "Create virtual ethernet adapter bound to physical adapter"
date: 2011-09-20
forum: Networking &amp; Wireless
---

### Post by MichiGreat on 2011-09-20
**Hi all!**

Let's assume you have a "eth0" physical ethernet adapter with four IP addresses, just like this:

192.168.1.1
192.168.1.2
200a:1111:1::1
200a:1111:1::2

Now I want services to listen on the IP addresses that end with 1 and another service (on the same TCP port!) to listen on the IP addresses that end with 2. I imagine having a second virtual ethernet adapter that is somehow bound to eth0 and gets a name similar, like eth0_1, to have a configuration like this:

eth0
192.168.1.1
200a:1111:1::1

eth0_1
192.168.1.2
200a:1111:1::2

Most services require lines like

INTERFACES="eth0"

in their /etc/default/... files, that's why I don't want to bind those services to IP addresses.

I tried it with a tun device (described [here]("http://backreference.org/2010/03/26/tuntap-interface-tutorial/")) like this:

openvpn --mktun tun2
ip link set tun2 up
ip addr add 192.168.1.2/24 dev tun2

But as soon the link is up, the system is not reachable anymore with TCP/IP.

Does anyone have an idea how I could solve that?

Greetings

*Michael*

---

### Post by MichiGreat on 2011-09-20
Meanwhile I found a method how to create a virtual ethernet interface. Simply with "ifconfig eth0:0 192.168.1.2 netmask 255.255.255.0". But if I try to add an IPv6 address, it is always added to eth0 instead of eth0:0. :-(

---

