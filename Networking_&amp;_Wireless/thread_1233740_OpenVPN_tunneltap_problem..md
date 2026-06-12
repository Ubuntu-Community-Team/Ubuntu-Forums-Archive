---
title: "OpenVPN tunnel/tap problem."
date: 2009-08-07
forum: Networking &amp; Wireless
---

### Post by Crafty Kisses on 2009-08-07
Alright so this is my setup right now I have two machines with two different subnets (obviously) but the problem is machine A can't ping machine B, but machine B can ping machine A, if that makes any sense. I read a very similar problem over at a different forum, so I did what some suggested and added a few lines myself, so what I did was open the following configuration file:
```
/etc/init.d/networking
```
Then once I had that configuration file open via nano, I looked around for a bit and decided to add the following lines:
```
openvpn --mktun --dev tun0
[...]
if ifup -a; then
	route add -net 192.168.1.254 netmask 255.255.255.0 gw Y2.X2.W2.Z2 tun1
else
[...]
```
So then I try to bring this up by running:
```
ifup tun0
```
Sadly I get the device not found, which is really confusing, this is the exact error I got actually:
```
**SIOCSIFADDR**: No such device
tun0: ERROR while getting interface flags: No such device
```
Now if anyone is interested, here's the kernel routing table for machine A which cannot ping machine B:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     W1.X1.Y1.Z1     255.255.255.0   UG    0      0        0 tun0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.1.254    0.0.0.0        UG    0      0        0 eth0
```
Alright so since I've gotten that out of the way, I then try to bring up the VPN connection on machine A by running:
```
192.168.1.0 # /etc/init.d/openvpn start
```
Then appears the VPN connection is up and running, but as to no surprise I cannot ping machine B. Then I start the VPN connection on machine B by running:
```
192.168.2.1 # /etc/init.d/openvpn start
```
An of course as I've stated I can ping machine A perfectly on machine B. Now I was doing a little searching, and I found a thread that said if I opened up the following configuration file:
```
/etc/openvpn/server.conf
```
Then I added following lines, as told by the person helping me:
```
push "route 192.168.1.0 255.255.255.0"
route 192.168.2.0 255.255.255.0
``` 
Then retried the ping, and still nothing. I also made sure that I have IP forwarding enabled, I did this by running the following:
```
echo 1 > /proc/sys/net/ipv4/ip_forward
```
I'd also like to say the routers have a NAT Gateway, so I'm not sure if that has something to do with it, but I highly doubt it. I've also tried suppressing some of the routes, and it's still not working. I'd also like to state that my **IP chains** look normal if anyone asks, here they are:
```
Chain INPUT (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination
    0     0 ACCEPT     all  --  lo     any     anywhere             anywhere
    0     0 ACCEPT     udp  --  ath0   any     anywhere             anywhere
```
Anyway, I'm kind of getting frustrated at this issue, so do you guys have any insight on this problem?

---

### Post by dmizer on 2009-08-07
If you want ping both ways through a VPN connection, you will need to set up a bridged vpn rather than a routed/tunneled vpn. I don't think it's possible to do what you want to do via tunneling: [http://openvpn.net/index.php/open-source/faq.html#bridge1](http://openvpn.net/index.php/open-source/faq.html#bridge1)

Unless I misunderstand what your configuration is. I've only recently begun to play with Openvpn, so my experience is a bit limited, but I'm fairly sure that with a VPN TUN device, the trafic is one way.

---

### Post by Crafty Kisses on 2009-08-09
So I changed the following:
```
dev tun
```
To the following:
```
dev tap0
```
Then as stated by the OpenVPN tutorial I looked at I allowed packets to access the new tap0 and br0 interface by running:
```
iptables -A INPUT -i tap0 -j ACCEPT
iptables -A INPUT -i br0 -j ACCEPT
iptables -A FORWARD -i br0 -j ACCEPT
```
So I setup my bridge, so I now have a bridged VPN connection, so I ran:
```
bridge-start
```
Then opened VPN, and to my surprise it works! Thanks a lot man. :)

---

### Post by dmizer on 2009-08-09
> **Codename said:**
> 
Then opened VPN, and to my surprise it works! Thanks a lot man. :)
Thought that would do it for you :-D

We seem to frequently be on the same page when experimenting with server stuff ... lol

---

### Post by Crafty Kisses on 2009-08-10
> **dmizer said:**
> Thought that would do it for you :-D

We seem to frequently be on the same page when experimenting with server stuff ... lol

Yes, I've noticed. ;-) Haha.

---

