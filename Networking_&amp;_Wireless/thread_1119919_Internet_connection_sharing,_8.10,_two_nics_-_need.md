---
title: "Internet connection sharing, 8.10, two nics - need help"
date: 2009-04-08
forum: Networking &amp; Wireless
---

### Post by srdjo on 2009-04-08
I tried to setup iptables, it didnt work, tried Firestarter, didnt work.

What do I have to do to get it working ?

I have two nics - eth0 and eth1

eth1 is my internet interface that gets the ip from dhcp. It is set correctly in /etc/network/intefaces

eth0 is my local interface, that has a static IP address 192.168.0.1 and that has dhcp server giving leases on it for my local network. It is set correctly in /etc/network/intefaces

My clients are getting correct IP addresses and can ping in lan, but cant ping the internet.


In openSuse, there is only one checkbox that you need to click and all is working instantly, w/o any setup at all.


Can anyone help me do this in Ubuntu 8.10 ?

---

### Post by Nostalos on 2009-04-08
Unless your ISP is routing public addresses behind that box for you, you have to enable IP Forwarding.  Otherwise your box just ignores packets not destined for itself.  Then you have to NAT the packets so that outbound connections appear to be coming from the outside address of your box.

> 
echo 1 > /proc/sys/net/ipv4/ip_forward
iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE



Should make it work.  modify /etc/sysctl.conf to permanently enable ip_forward


[COLOR="Red"]DISCLAIMER!![/COLOR]
This is NOT secure, this just makes it work.   You will need to enable some type of firewall policy to make this remotely secure.  There are plenty of HOWTO's on doing just that.  Quick Google search should give you plenty of reading.

---

### Post by srdjo on 2009-04-08
It goes like this:


ISP -> Router(public ip) -> eth1 {dhcp client/private IP} (server) etho -> switch -> lan

Will it work ?

---

### Post by srdjo on 2009-04-08
It is not working :(

---

### Post by srdjo on 2009-04-09
Can anyone help me with this ?

P.S. I see in ufw firewall log that it is blocking every in out and filter from client ip ?

What might be the problem ?

---

### Post by wycito on 2009-04-09
Pls post your /etc/network/interfaces file ...

---

### Post by srdjo on 2009-04-09
auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp

auto eth0
iface eth0 inet static
        address 192.168.0.1
        netmask 255.255.255.0

---

### Post by Spider7 on 2009-04-09
> **srdjo said:**
> It goes like this:


ISP -> Router(public ip) -> eth1 {dhcp client/private IP} (server) etho -> switch -> lan

Will it work ?

I assume your setup is:

public-ip:Router:private-ip <--------> eth1:Server:eth0 <------> client.

and you can ping 
- from server to router-private-ip
- between client and server-eth0

Can you ping from client to server eth1 address? if not, check the routing table on the client.
if that works, can you ping from client to router private ip? if not, it's likely the server setup. Unless you have route setup to the 2nd private network, you'll need NAT on the server.

---

### Post by srdjo on 2009-04-09
It is working now.

I used this guide

[https://help.ubuntu.com/8.04/serverguide/C/firewall.html](https://help.ubuntu.com/8.04/serverguide/C/firewall.html)

to setup ufw nat.

and I also forgot to set ISP DNS server on my internal lan dhcp server (because I dont have dns server).

---

### Post by inobe on 2009-04-09
i simply edit eth0's connection.

under IPv4 settings i change from "automatic DHCP" to "shared to all computers"

fast and simple, in fact i never read anything to lead me there, i simply checked the settings :lol:

---

### Post by Nostalos on 2009-04-09
I didn't realize you had ufw enabled already.  Glad you got it working.

---

