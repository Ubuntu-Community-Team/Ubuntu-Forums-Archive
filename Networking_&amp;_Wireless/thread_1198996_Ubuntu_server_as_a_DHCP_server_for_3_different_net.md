---
title: "Ubuntu server as a DHCP server for 3 different networks"
date: 2009-06-28
forum: Networking &amp; Wireless
---

### Post by madfrenzy on 2009-06-28
Hi all,
I was wondering if it is possible to configure an ubuntu server to be a DHCP server for 3 different networks (as shown in the pic)cause I wanted to implement this at my work. also is there a way to implement routing also??.

[IMG]http://lookpic.com/i/875/rc8RsK11.jpeg[/IMG]

---

### Post by puppywhacker on 2009-06-28
Sure, assign ip-addresses like 10.1.0.1 to the interfaces first. don't use 11 or 12, since only 10.x.x.x and 172.16.x.x and 192.168.x.x are reserved  private ranges.

After that you can assign in /etc/dhcp3/dhcpd.conf three subnets to handout ip addresses to the clients. the routers option will set the default gateway to the outside world. the other routing rules should be automatically set when you assign ip addresses.

subnet 10.1.0.0 netmask 255.255.0.0 {
  option routers 10.1.0.1;
}
subnet 10.2.0.0 netmask 255.255.0.0 {
  option routers 10.2.0.1;
}
subnet 10.3.0.0 netmask 255.255.0.0 {
  option routers 10.3.0.1;
}

next you have to enable ipforwarding in sysctl and add an masquerading rule in iptables to allow access to the internet.

sysctl -w net.ipv4.conf.all.forwarding=1

iptables -t nat -A POSTROUTING -o eth3 -j MASQUERADE
iptables-save

---

### Post by madfrenzy on 2009-06-28
thank you very much on your reply, but do you know a link to a more detailed tutorial?? cause I'm a bit new to ubuntu :(

---

### Post by puppywhacker on 2009-06-28
For a large part the following howto should help you on your way

[https://help.ubuntu.com/community/dhcp3-server]("https://help.ubuntu.com/community/dhcp3-server")

Since it only describes how to set up the dhcp server you still need the last two steps I wrote on sysctl and iptables to get the internet sharing up and running.

---

### Post by madfrenzy on 2009-06-28
Thank you, I'll try it and I'll reply with what will happen :) by the way how to tell the DHCP server that on eth0 it will distribute 10.1.0.0 and on eth1 it will distribute 10.2.0.0 etc. ??

---

### Post by puppywhacker on 2009-06-28
dhcpd knows which ip-range to use based on the ip-addresses set for each interface. So if eth0 has address 10.1.0.1 with netmask 255.255.0.0 (same as /16) your network will fit in the 10.1.x.x network. dhcpd will have a subnet configuration in which it can handout addresses from that range.

---

