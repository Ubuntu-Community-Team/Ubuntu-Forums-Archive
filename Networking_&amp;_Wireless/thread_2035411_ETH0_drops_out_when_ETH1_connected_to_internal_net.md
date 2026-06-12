---
title: "ETH0 drops out when ETH1 connected to internal network switch."
date: 2012-07-30
forum: Networking &amp; Wireless
---

### Post by duplex50 on 2012-07-30
Hello there! This is my first post to any forum, EVER!
 
I have been working with Ubuntu linux for several months now. I have already successfully configured a Snort box for intrusion detection.
 
Currently, I am working to configure a Poweredge 2650 as a Firewall for my home network. Installed is Ubuntu Server 12. I have two NICs, ETH0 and ETH1. ETH0 is the external interface and is configured with a static address (192.168.254.2) on 192.168.254.0/24 network. ETH0 is connected directly to the DSL modem. ETH1 is the internal interface and configured with a static address (192.168.1.23) on 192.168.1.0/24 network.
 
While SUCCESSFULLY pinging out to the internet ([www.google.com]("http://www.google.com")) on ETH0, as soon as I connect ETH1 to the switch on my internal network, the connection drops (MSG: Operation not permitted). I can then ping internal network IPs, but can no longer get out to the internet on ETH0. Default gw route added for ETH0. Default gateway (DSL modem) 192.168.254.254.
 
NetworkManager.conf is currently set to manager network connections.
 
What am I missing? Why does connecting ETH1 to internal network cause ETH0 to drop out?
 
I can provide any information needed for suggestions on resolving this issue.
 
Thanks in advance!
 
While ETH0 is successfully pinging google.com, route command shows the default gw for ETH0 as the DSL modem's name: speedstream.domain.  When connecting ETH1 to switch, route command shows that the default gw for ETH0 is now just it's IP address: 192.168.254.254.  DNS issue?

---

### Post by Kirk Schnable on 2012-07-30
Nah, DNS wouldn't affect your ability to ping IP addresses.

This may seem redundant, but please do so, just so we can make sure something didn't slip past you.  Can you provide the output of the following commands **before** and **after** plugging in the second interface?

```
ifconfig
```

```
route -n
```

Thanks,
Kirk

---

### Post by duplex50 on 2012-07-30
route

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         speedstream.dom 0.0.0.0         UG    0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
192.168.254.0   *               255.255.255.0   U     1      0        0 eth0

route -n

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.254.254 0.0.0.0         UG    0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.254.0   0.0.0.0 

/etc/network/interfaces

auto lo
iface lo inet loopback

iface eth0 inet static
        address 192.168.254.2
        network 192.168.254.0
        netmask 255.255.255.0
        broadcast 192.168.254.255

dns-nameservers 192.168.254.254

iface eth1 inet static
        address 192.168.1.23
        network 192.168.1.0
        netmask 255.255.255.0

---

### Post by duplex50 on 2012-07-30
ABOVE IS JUST eth0 UP, With a valid connection to the internet.

BELOW IS HOW THE routing table changes when connecting eth1 to the local network.

route

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         192.168.254.254 0.0.0.0         UG    0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
localnet        *               255.255.255.0   U     1      0        0 eth1
192.168.254.0   *               255.255.255.0   U     1      0        0 eth0

route -n

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         192.168.254.254 0.0.0.0         UG    0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
localnet        *               255.255.255.0   U     1      0        0 eth1
192.168.254.0   *               255.255.255.0   U     1      0        0 eth0

ALSO

/etc/resolv.conf

nameserver 192.168.254.254
nameserver 4.2.2.2


My issue persists.  As soon as I connect eth1 to local network via Cisco Catalyst 2980G, eth0 drops internet connection.

I have also remove network manager so it can't bullocks up the works.   

Any suggestions are truly appreciated.


Regards,

---

### Post by duplex50 on 2012-07-30
I also created a separate VLAN on my Cisco Catalyst 2980G and plugged in eth1 there.  To my dismay, the same behavior occured.

---

