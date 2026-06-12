---
title: "Simple question about my first bridged OpenVPN"
date: 2010-09-25
forum: Networking &amp; Wireless
---

### Post by Telémakhos on 2010-09-25
Hi guys,

I'm in the way to set up my very first VPN (Bridged OpenVPN) to extend my little office network. At the office we've a linksys WRT54GL acting as a Gateway/Firewall and the newtwork type I want is 192.168.1/24 for all the private network. Now I have:

192.168.1.1 (Router/Gateway)
192.168.1.2 (Ubuntu Server 10.4 with OpenVPN server)
192.168.1.X (The clients)

**/etc/network/interfaces** 

```

auto lo br0
iface lo inet loopback

iface br0 inet static
[COLOR="Green"]**address 192.168.1.2**[/COLOR]
netmask 255.255.255.0
gateway 192.168.1.1
bridge_ports eth0

iface eth0 inet manual
up ifconfig $IFACE 0.0.0.0 up
up ip link set $IFACE promisc on
down ip link set $IFACE promisc off
down ifconfig $IFACE down
```

Should the bridged interface have the same address as the machine where is installed Ubuntu Sever/OpenVPN server? or should I use another one? My router is assigning IP's from 192.168.1.2 (beginning with the server)...

---

### Post by Telémakhos on 2010-09-25
Cant believe nobody knows this... I know it's very basic but I need your help please. I've been following this HowTo but I'm stuck in the Configuration section. I need to know how to set up my network interfaces.

[https://help.ubuntu.com/10.04/serverguide/C/openvpn.html](https://help.ubuntu.com/10.04/serverguide/C/openvpn.html)

Can you please help to figure out the next steps?

Thanks

---

### Post by Telémakhos on 2010-09-25
Ok guys, I found this tutorial. 

[http://www.cryptolife.org/index.php/Openvpn_roadwarrior_bridged_mode_howto](http://www.cryptolife.org/index.php/Openvpn_roadwarrior_bridged_mode_howto)

It's perfect for what I want to do. Didnt even know its named Roadwarrior VPN...

---

