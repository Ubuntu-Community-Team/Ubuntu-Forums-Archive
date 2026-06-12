---
title: "Ubuntu as a gateway, how to block the outgoing?"
date: 2010-11-29
forum: Networking &amp; Wireless
---

### Post by September on 2010-11-29
Hi people,

I have a network structure like this: there are around 50 computers in a subnet. They obtain ip's from a dhcp server and they all get 10.1.18.x

I have set one of the computers as a server (static ip 10.1.18.245) and lets call all other 49 computers as clients.
In the clients, I have set the /etc/network/interfaces like this:

```
auto eth0
iface eth0 inet dhcp
up route del default
up route add default gw 10.1.18.245

```Whit this, all clients get dynamic ip from the dhcp server (i dont know where it is) and they also receive the dns servers from the dhcp. They only send all traffic through the server (10.1.18.245).

I can successfully drop the internet completely for clients by doing this on the server:

```
echo 0 > /proc/sys/net/ipv4/ip_forward
```They can still access 10.1.18.x ips as that is what I desire.

Now, when I want to block a specific ip for the clients, I believe I need to do something with iptables.

I have so far tried (on the server)

```
iptables -A FORWARD -d 66.66.66.66 -j DROP
```to block the clients from reaching 66.66.66.66, which is an ip in the internet. But it does not work.

The problem may be the server (10.1.18.245) being the 'gateway' for clients. In this scenario how may I block a destination ip for clients? Does the packets sent by the clients managed by FORWARD?

PS: I cannot access any switch/router or any other hardware to design a better scenario for this 50 computers. I am telling this because there is possibility that I may receive responses like "why dont you do it like this, etc", though I appreciate such responses as they teach me something.

PS2: all 50 machines have ubuntu 10.10 desktop edition (including the server 10.1.18.245)

---

