---
title: "Ubuntu problem bonding 3G modems"
date: 2011-05-21
forum: Networking &amp; Wireless
---

### Post by j.barajas on 2011-05-21
Hi, I need some help I trying to bond two 3G modems but I cant Im really new in this matther so I really nedd your help. This is the error that appears
ubu@ubu-AOD255E:~$ sudo /etc/init.d/networking restart

 * Reconfiguring network interfaces...                                          Ignoring unknown interface ppp0=ppp0.
Ignoring unknown interface ppp1=ppp1.
There is already a pid file /var/run/dhclient.bond0.pid with pid 2181
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/bond0/00:00:00:00:00:00
Sending on   LPF/bond0/00:00:00:00:00:00
Sending on   Socket/fallback
DHCPDISCOVER on bond0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on bond0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on bond0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on bond0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on bond0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on bond0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on bond0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on bond0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on bond0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
Master 'bond0': Error: set hw address failed
Master 'bond0', Slave 'ppp0': Error: Enslave failed
Master 'bond0': Error: set hw address failed
Master 'bond0', Slave 'ppp1': Error: Enslave failed

Failed to bring up bond0.

This is the configuration that I made to /etc/network/interfaces

  GNU nano 2.2.4         File: /etc/network/interfaces                          

# loopback

auto lo

iface lo inet loopback

# - ppp0

#auto ppp0

#iface ppp0 inet dhcp

# - ppp1

#auto ppp1

#iface ppp1 inet dhcp

auto bond0
                  
#iface ppp0 inet dhcp

# - ppp1

#auto ppp1

#iface ppp1 inet dhcp

auto bond0

iface bond0 inet dhcp

       address 10.40.210.45

       gateway 10.64.64.64

       network 10.64.64.64

       netmask 255.255.255.255
     
slaves ppp0 ppp1


       bond-mode 3

       bond-miimon 100

       bond-primary ppp0 ppp1

       up ifenslave bond0 ppp0 ppp1


My first problem was this 
 * Reconfiguring network interfaces...                                          Ignoring unknown interface ppp0=ppp0.
Ignoring unknown interface ppp1=ppp1.
SIOCADDRT: File exists
Failed to bring up bond0.

I solve this issue changing the gateways, I dont know if I make some wrog that why I cant bond the 3G modems.
I hope you can help me.

---

### Post by headvampyre@hotmail.co.uk on 2011-05-21
Have you tried rebooting since creating the bonds?

I remember having to remove a file (this was 4 months ago so i cant remember exactly where it was), a reboot should fix this.

Also - your using DHCP for addresses, yet setting the IP, gateway, network and netmask manually. That is usually used for setting a static ip.

---

### Post by headvampyre@hotmail.co.uk on 2011-05-21
Also, looking at my Ethernet config file, you might want to add:

iface ppp0 inet manual

iface ppp1 inet manual

Heres my config:

auto lo
iface lo inet loopback

iface eth0 inet manual

iface eth1 inet manual

auto bond0
iface bond0 inet static
        bond_miimon 100
        bond_mode balance-tlb
        address 11.22.33.45
        netmask 255.255.255.0
        gateway 11.22.33.44
        up /sbin/ifenslave bond0 eth0 eth1
	down /sbin/ifenslave -d bond0 eth0 eth1

You could probably cut out the addresses, netmask and gateway if you changed:

iface bond0 inet static

to:

iface bond0 inet dhcp

---

### Post by testdemo on 2011-07-05
I have the same problem. Can tell me how to do it?

---

