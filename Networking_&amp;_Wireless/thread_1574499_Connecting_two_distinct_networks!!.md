---
title: "Connecting two distinct networks!!"
date: 2010-09-14
forum: Networking &amp; Wireless
---

### Post by parleg on 2010-09-14
Help me with this network!!

Background -
I have two ISP - DSL service from local telco and Broadband service from cable provider.
DSL is networked from a netgear DG834G wireless router on 192.168.2.1 - 192.168.2.255 network (SJNET).
The Cable provider service is networked from a ASUS router on 192.168.1.1 - 192.168.1.1255 network (SJCOM).

I have 3 machines running various flavors of Linux on the 192.168.2.1 DSL network. 
These all are working fine as expected. 
I do not have wired access to [192.168.1.0/24]("http://192.168.1.0/24") network from the Linux machines.

I have a Dlink wireless PCI card on one of the Ubuntu machine.

Following is the /etc/network/interfaces

-- cut --
vrk@celeron:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.2.3
netmask 255.255.255.0
network 192.168.2.0
broadcast 192.168.2.255
gateway 192.168.2.1

#auto wlan0
iface wlan0 inet static
address 192.168.1.2
gateway 192.168.1.1
dns-nameservers 192.168.1.1
netmask 255.255.255.0
wpa-driver wext
wpa-ssid SJCOM
wpa-ap-scan 2
wpa-proto RSN
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk "1234567890"

vrk@celeron:~$ 

-- paste --

I am trying to figure out - what is the best way to configure the network so that all machines are visible to each other
i.e. Any laptop connected to the SJCOM network can access any linux machine on the SJNET network.

I tried following the steps in [http://linux.about.com/od/ubusrv_doc/a/ubusg18t03.htm](http://linux.about.com/od/ubusrv_doc/a/ubusg18t03.htm) (but didn't succeed).
Tried setting up static routes on each ofrouters to the other one - but couldn't traceroute back to.

I would really appreciate if someone could point me to the right direction to get this configured correctly.

Thanks.

---

### Post by Iowan on 2010-09-14
I haven't read through everything (yet), but a "default gateway" is where "all other" traffic goes. Having two gateways generally causes problems. Ordinarily, the internet-facing interface is defined as the gateway. With two...?

---

### Post by dmizer on 2010-09-14
Two ISP's means you have two completely separate networks. In order for traffic to pass between all machines, both networks need to be joined somewhere. Generally, that's done with a load balancer at the network source.

Something like this
```

SJNET ---NIC1
         Load balancer NIC3 --- Hub ---- All other machines.
SJCOM ---NIC2

```

Alternatively, you could configure a VPN server on one of the machines connected to the SJNET network. Then the machines on the SJCOM network can become VPN clients.

I don't know enough about your setup to really recommend an appropriate method, but if you can't physically join both networks somewhere, then your best solution is probably a VPN.

---

