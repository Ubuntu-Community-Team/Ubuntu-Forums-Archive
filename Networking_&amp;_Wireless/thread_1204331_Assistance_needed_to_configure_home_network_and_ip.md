---
title: "Assistance needed to configure home network and iptables"
date: 2009-07-04
forum: Networking &amp; Wireless
---

### Post by Sky Pixie on 2009-07-04
The objective is to configure a multi computer home network to use a dedicated Squid caching proxy.

Cable Modem > Computer #1 > DIR-825 Router > Computers #2-5

Computer #1 runs Ubuntu Server 8.04 and Squid 3.0STABLE15.  There are two NICs - NIC0 and NIC1.  The cable modem is connected to NIC0 and the DIR-825 router is connected to NIC1.
NIC0 - eth0
NIC1 - eth1

The file /etc/network/interfaces is as follows:
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

# The secondary network interface
auto eth1
iface eth1 inet static
address 192.168.0.2
gateway 192.168.0.1
netmask 255.255.255.248
network 192.168.0.0
broadcast 192.168.0.7

```

The router WAN is as follows:
IP 192.168.0.3     (Also tried 192.168.0.2)
Netmask 255.255.255.248
Gateway 192.168.0.1

The router LAN is as follows:
Router IP 192.168.1.2
Netmask 255.255.255.0

The router assigns IP addresses to Computers #2-5 on 192.168.1.xxx

Currently, I suspect Squid is properly configured.

On Computer #1, I did the following to iptables:
```

sudo iptables –t nat –A POSTROUTING –o eth0 –j MASQUERADE 
sudo iptables –A FORWARD –s 192.168.0.0/16 –j ACCEPT 
sudo iptables –A FORWARD –d 192.168.0.0/16 –j ACCEPT
sudo iptables –A FORWARD –s ! 192.168.0.0/16 –j DROP

sudo iptables -t nat -A PREROUTING -i eth1 -p tcp -m tcp --dport 80 -j DNAT --to-destination 192.168.0.2:3128
sudo iptables -t nat -A PREROUTING -i eth0 -p tcp -m tcp --dport 80 -j REDIRECT --to-ports 3128

```

I enabled port forwarding in /etc/sysctl.conf and rebooted the computer.

From Computer #2 I can ping:
the router at 192.168.1.2
the WAN at 192.168.0.3
NIC1 at 192.168.0.2

From Computer #2 I cannot ping:
NIC0

From Computer #1 I can ping:
NIC0
NIC1

From Computer #1 I cannot ping:
the router
the WAN
Computer #2

I suspect an improperly configured firewall is the problem.

Thank you in advance.

---

### Post by computer13137 on 2009-07-04
You seem to have prepared well, however, have you forgotten to enable packet forwarding in the kernel?  You mentioned something about editing sysctl.conf, which I never edited on my router, however running this command at boot was necessary in my setup.

```
echo 1 > /proc/sys/net/ipv4/ip_forward
```

Also, I know iptables can be configured in various different ways, but this is how my router is setup.

```
iptables --table nat --append POSTROUTING --out-interface eth0 -j MASQUERADE
iptables --append FORWARD --in-interface eth1 -j ACCEPT
```

I have never run a Squid proxy server, so I'm not sure if this particular method will work for your setup or not.  I'll try to help you as best I can if these solutions don't help.

Cheers,
Kirk

---

### Post by Sky Pixie on 2009-07-05
Thank you Kirk.  I know what I must know and not much more.

It is my understanding the echo command is temporary while adding lines to /etc/sysctl.conf is permanent.  This
[thread](http://ubuntuforums.org/showthread.php?t=324001) suggests adding
```
net.ipv4.conf.all.forwarding=1
```
to /etc/sysctl.conf

I may or may not have added
```
net.ipv4.conf.default.forwarding=1
```
at the suggestion of a post at another website.

I will double check the /etc/sysctl.conf file to see if that is what I did.

---

### Post by ROBarber on 2009-07-05
Sky Pixie, I am doing almost the same configuration as yours. The difference are: I use Firestarter to take care of ICS and wicd to take care of first NIC configration (connected to the Internet). I add manually to /etc/network/interfaces the address (10.1.1.1), the netmask (255.255.255.0) and the gateway for the second NIC (shame on me  I forgot the numbers :D). I configured the router with the address 10.1.1.2, gateway and primary DNS **10.1.1.1**, and with DHCP enabled to give to the machines in the LAN addresses. But it didn't work, no conmection to the Internet. If I connect directly another machine to the Ubuntu server with the same configuration as I did for router, everything works just fine.

I saw that the address of your server second NIC is different from the gateway used to set up router (192.168.0.2 and 192.168.0.1). If you set the router IP to 192.168.0.2 it is the same as the NIC1 has, and this an IP conflict.

I think you should try to set the router's IP to 192.168.0.3 (or something greater) and the gateway and primary DNS to 192.168.0.2 which is the address of NIC1, and to enable DHCP to give addresses in the LAN starting from 192.168.0.10 (or whatever you want).

If you make your router working, please share to us your data on how you configure it. I'm interested to make mine working, too.

Good luck,
ROBarber

---

### Post by computer13137 on 2009-07-05
ROBarber: It sounds like you need to also define your default gateway as 10.1.1.1.  I didn't see any mention of your having done that.

Depending on your router, there should be a way to do it.  Otherwise you may have to set static IPs on every machine, so you can define the gateway yourself.

Cheers,
Kirk

---

### Post by ROBarber on 2009-07-06
Yes, I set the gateway for the router as 10.1.1.1 (it is in bold in my last comment) but no luck so far

---

### Post by Sky Pixie on 2009-07-06
I changed the Gateway on the router WAN.

The router WAN is as follows:
IP 192.168.0.3
Netmask 255.255.255.248
Gateway 192.168.0.2

The Gateway is now the IP address of NIC1.

I added
```
net.ipv4.conf.all.forwarding=1
```
to /etc/sysctl.conf

I can now ping eth0 from Computer #2, but I'm still unable to ping the outside world such as Google.

I created a file to save the firewall configuration by following steps found [here](https://help.ubuntu.com/community/IptablesHowTo).

After setting firewall rules using Guarddog and then adding the rules listed in my first post,
```
sudo sh -c "iptables-save > /etc/iptables.rules"
```

```

#!/bin/sh
iptables-restore < /etc/iptables.rules
exit 0

```

```
sudo chmod +x /etc/network/if-pre-up.d/iptablesrestore
```

It's time for more research...

---

### Post by alphacrucis2 on 2009-07-06
> **Sky Pixie said:**
> I changed the Gateway on the router WAN.

The router WAN is as follows:
IP 192.168.0.3
Netmask 255.255.255.248
Gateway 192.168.0.2

The Gateway is now the IP address of NIC1.


You should not be specifying a default gateway on NIC1. That will conflict with default gateway on NIC 0 which is the real default gateway for your server. Also make sure that address and subnet picked up by DHCP via NIC0 does not conflict with the subnet on NIC1. NIC0 and NIC1 [COLOR="Red"]**MUST**[/COLOR] be in different subnets. What is the output from:

```
route -n
```

---

### Post by Sky Pixie on 2009-07-07
> **alphacrucis2 said:**
> You should not be specifying a default gateway on NIC1. That will conflict with default gateway on NIC 0 which is the real default gateway for your server. Also make sure that address and subnet picked up by DHCP via NIC0 does not conflict with the subnet on NIC1. NIC0 and NIC1 [COLOR="Red"]**MUST**[/COLOR] be in different subnets. What is the output from:

```
route -n
```
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.248 U     0      0        0 eth1
xx.xx.96.0      0.0.0.0         255.255.248.0   U     0      0        0 eth0
0.0.0.0         xx.xx.96.1      0.0.0.0         UG    100    0        0 eth0

```
I commented out part of the destination IP to obscure the dynamic IP given to me by the ISP.  The default gateway for eth1 has been commented out in /etc/network/interfaces.  Thank you for your help.

---

