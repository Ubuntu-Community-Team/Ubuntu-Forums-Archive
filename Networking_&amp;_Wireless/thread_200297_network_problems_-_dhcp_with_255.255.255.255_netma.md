---
title: "network problems - dhcp with 255.255.255.255 netmask"
date: 2006-06-20
forum: Networking &amp; Wireless
---

### Post by grw on 2006-06-20
My network was unreachable for a long time due to a DHCP bug relating to networks with a netmask of 255.255.255.255. (Don't know why Ubuntu haven't fixed this problem). I thought I had finally found a solution (see below) and everything was working fine for a day or two. But now the network is unreachable again (Windows works). 

For some reason, I am unable to activate eth0. I have tried using the gui (admin -- networking) but it just seems to deactivate itself shortly after I activate it. Any ideas? Thanks

My network administrator gave this fix for teh dhcp bug. I edited /etc/dhcp3/dhclient-script
adding this hack:

for router in $new_routers; do
# !!! hack
if [ "$new_subnet_arg" == 'netmask 255.255.255.255' ]; then
	route add -host $router dev $interface
fi
# !!! end of hack
                route add default dev $interface gw $router $metric_arg
            done

See also this bug report with a slightly different solution: [https://launchpad.net/distros/ubuntu...cp3/+bug/33382](https://launchpad.net/distros/ubuntu...cp3/+bug/33382)

---

### Post by simonn on 2006-06-20
255.255.255.255 is not a valid netmask!

Have a read: [http://en.wikipedia.org/wiki/Netmask](http://en.wikipedia.org/wiki/Netmask)

---

### Post by grw on 2006-06-20
Lots of people have told me that 255.255.255.255 is not a valid netmask.

But I think it is. It's just rare - part of point to point networks. 
The network adminsistrator here assures me that it is valid. Windows works with this netmask. Ubuntu worked for a while...

Here's a quote from the bug report I cite in my first post- 'dhclient-scripts fails on point-to-point network configurations':

"well, the range can be bigger. but essentialy all machines get a dhcp address
with netmask 255.255.255.255 and a gateway address, so all communication
is to that gateway, which is a firewall and filters unwanted traffic. also the
switch is reconfigured so each machine is in it is own private vlan, and can
only talk to the gateway / firewall.

this configuration is usd in high security environment, where you want to
police all machine to machine traffic, but it is also used in much simpler
scenario: server hosting. here you don't want to one customer to attack
any other customer with arp spoofing or anything like that. so each
customer is limited to a network with only him and the gateway. but you
can't use a /30 network with 4 addresses per machine, that would be a
huge waste of ip space. so what providers do point to point configuration
with one official address for the server connected to the gateway which
is also the direction for the default route."

---

### Post by linuchsan on 2006-06-20
You can add the route:
route add -host 255.255.255.255 dev eth0

---

### Post by grw on 2006-06-20
I tried route add -host 255.255.255.255 dev eth0 ... but no luck

I wonder if I haven't stuffed up my /etc/dhcp3/dhclient-script file (there's a syntax error in the file where I changed it)?
Where can I get another one?

Here's some ifconfig output and so on,  in case it helps anyone.
Thanks again

gwyn@gwyn:~$ lspci | grep Eth
0000:02:04.0 Ethernet controller: Intel Corporation 82557/8/9 [Ethernet Pro 100] (rev 08)
gwyn@gwyn:~$ lsmod |grep mii
mii                     5888  1 e100

gwyn@gwyn:~$ ping 10.0.8.1
connect: Network is unreachable
gwyn@gwyn:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:20:E0:6E:A0:66
          inet addr:10.0.9.40  Bcast:10.0.9.40  Mask:255.255.255.255
          inet6 addr: fe80::220:e0ff:fe6e:a066/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:187 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:33087 (32.3 KiB)  TX bytes:1152 (1.1 KiB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:472 (472.0 b)  TX bytes:472 (472.0 b)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

gwyn@gwyn:~$ sudo route add -host 255.255.255.255 dev eth0
gwyn@gwyn:~$ ping 10.0.8.1
connect: Network is unreachable

gwyn@gwyn:~$ sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

/etc/dhcp3/dhclient-script: line 204: syntax error near unexpected token `done'/etc/dhcp3/dhclient-script: line 204: `            done'
Listening on LPF/eth0/00:20:e0:6e:a0:66
Sending on   LPF/eth0/00:20:e0:6e:a0:66
Sending on   Socket/fallback
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 10.0.8.1
/etc/dhcp3/dhclient-script: line 204: syntax error near unexpected token `done'/etc/dhcp3/dhclient-script: line 204: `            done'
dhclient.c(2062): null pointer
DHCPDECLINE on eth0 to 255.255.255.255 port 67
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPOFFER from 10.0.8.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 10.0.8.1
/etc/dhcp3/dhclient-script: line 204: syntax error near unexpected token `done'/etc/dhcp3/dhclient-script: line 204: `            done'
dhclient.c(2062): null pointer
DHCPDECLINE on eth0 to 255.255.255.255 port 67
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPOFFER from 10.0.8.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 10.0.8.1
/etc/dhcp3/dhclient-script: line 204: syntax error near unexpected token `done'/etc/dhcp3/dhclient-script: line 204: `            done'
dhclient.c(2062): null pointer
DHCPDECLINE on eth0 to 255.255.255.255 port 67
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPOFFER from 10.0.8.1

gwyn@gwyn:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

---

