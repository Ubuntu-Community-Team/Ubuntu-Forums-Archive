---
title: "Manual route for VPNs"
date: 2010-03-24
forum: Networking &amp; Wireless
---

### Post by sparky-steve on 2010-03-24
Hello,

I use my computer as a gateway to the internet for the rest of the house which is split into two LANs. I also have VPN's linking the office side of the LAN to a remote site.

All of the PC's other than mine that should have access to the VPN works, but my PC doesnt and I firmly believe this is because I need to add a static route.

ping 192.168.10.1 doesnt work but ping -I eth2 192.168.10.1 does.

192.168.10.1 is the remote router on the other side of the VPN.

I've tried this route:

```
route add -net 192.168.10.0 netmask 255.255.255.0 gw 192.168.1.1 dev eth2
```

192.168.1.1 is my computer... the gateway for the rest of the house/office.

My computer has a quad NIC, only 3 ports are used. WAN, LAN1 and LAN2.

Aside from this routing issue, I have everything working perfectly.

Any assistance out there?

SS

---

### Post by Iowan on 2010-03-24
Network Manager has the option to add routes (though I've never used it).

---

### Post by Alabamaschalk on 2010-03-24
This
[http://geekyprojects.com/ubuntu/ubuntu-vpn-connection/](http://geekyprojects.com/ubuntu/ubuntu-vpn-connection/)
Is a description on how to manually route.
But you should not listen to me because I haven't tried either.

---

### Post by sparky-steve on 2010-03-25
Hi & thanks for taking the time to add your thoughts.

Unfortunately, I dont think I've explained my problem too well.

I have two gateway machines, separated by the internet. They each run an IPSEC VPN to each other.

There are multiple machines behind each gateway machine, and all of those machines can reach the internet and any of the services on the remote VPN via local IP (192.168.1.10 can ping 192.168.2.10 for example).

However, the two gateways themselves cannot ping each other or any machine on the remote LAN via VPN; That said, if I change the ping source interface, I can ping the other side.

for example, from machine 192.168.1.1

```
ping 192.168.2.1
```

does not work, but

```
ping -I eth1 192.168.2.1
```

does work. eth1 is the LAN interface with IP 192.168.1.1

So, I am wondering if a simple route is required for the gateway machines to utilise the VPN, or whether I've not fully configured IPSEC in some way.

Help is appreciated.

SS

---

### Post by sparky-steve on 2010-03-26
Well, it seems like the answer was simple, even if evasive.

all that is required in the ipsec.conf file is the following code:

```
leftsourceip=192.168.1.x
....
rightsourceip=192.168.2.x
```

Therefore, a working example of a LAN-to-LAN ipsec.conf is as follows (and should be duplicated at both sites)

remove all #comments including the #

```
conn here-to-there #just a name
 authby=secret #im using the /etc/ipsec.secrets file for psk
 left=1.2.3.4 #the remote (static) IP address
 leftsubnet=192.168.5.0/24 #the network address
 leftnexthop=%defaultroute 
 leftsourceip=192.168.5.1 #this is the part that allows the gateway to route over IPSEC to the other LAN!!!! :-)
 right=2.3.4.5 #my (static) IP address
 rightsubnet=192.168.1.0/24 #my network address
 rightnexthop=%defaultroute
 rightsourceip=192.168.1.1 #this machines LAN IP
 auto=start
```

I hope this might help someone in the future.

SS

---

