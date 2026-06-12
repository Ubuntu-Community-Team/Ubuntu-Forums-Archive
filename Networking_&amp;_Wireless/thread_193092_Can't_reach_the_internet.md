---
title: "Can't reach the internet"
date: 2006-06-09
forum: Networking &amp; Wireless
---

### Post by ales on 2006-06-09
Can't connect to internet. In 5.10 on same HW no problem. Now after fresh installation no problem, after installing updates network is not working. Networking shows that Lan is online and also router. But it can't reach the internet. This is what I got? Is it bug in Dapper?

dreamwalker@dreamwalker:~$ sudo dhclient
Password:
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth1/00:13:d4:c2:34:34
Sending on   LPF/eth1/00:13:d4:c2:34:34
Sending on   Socket/fallback
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPNAK from 10.0.0.138
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPOFFER from 10.0.0.138
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPACK from 10.0.0.138
SIOCADDRT: Network is unreachable
bound to 212.55.250.18 -- renewal in 34241 seconds.
dreamwalker@dreamwalker:~$

dreamwalker@dreamwalker:~$ ping 82.211.81.166
connect: Network is unreachable
dreamwalker@dreamwalker:~$

---

### Post by Fammy on 2006-06-09
I'm getting a similar problem on a fresh install of Dapper. I can ping the router and local network, but not the outside world. If I open the Network manager, and change a setting (sometimes just inspect the wireless card), it'll start working. I'm using a Linksys WMP11 PCI wireless card. I've tried everything. Worked fine in the last two releases...

---

### Post by ales on 2006-06-09
Hmm I have got the ALcatel Thomson Speedtouch 530i router, and asus A8nsli deluxe MB with tho ethernets, and problems with connection. Can't understand why. Card has in networking tools assigned IP....
I think it's bug. 5.10 works 6.06 no?

---

### Post by pnael on 2006-06-09
Hello,

It looks like a routing problem. It seems that you have 2 network cards
since your dhcp client use eth1. Please provide the output of :
"ifconfig -a" and "route"

cheers
Philippe

---

### Post by ales on 2006-06-09
dreamwalker@dreamwalker:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:D4:C2:28:FF
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:225 Base address:0x6000

eth1      Link encap:Ethernet  HWaddr 00:13:D4:C2:34:34
          inet addr:212.55.250.18  Bcast:212.55.250.255  Mask:255.255.255.0
          inet6 addr: fe80::213:d4ff:fec2:3434/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1820 (1.7 KiB)  TX bytes:1722 (1.6 KiB)
          Interrupt:58

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:272 (272.0 b)  TX bytes:272 (272.0 b)

dreamwalker@dreamwalker:~$
dreamwalker@dreamwalker:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
212.55.250.0    *               255.255.255.0   U     0      0        0 eth1
dreamwalker@dreamwalker:~$

 this is what i got

---

### Post by Slim Odds on 2006-06-09
[quote=pnael]Hello,

It looks like a routing problem. It seems that you have 2 network cards
since your dhcp client use eth1. Please provide the output of :
"ifconfig -a" and "route"

cheers
Philippe[/quote]

"route -n" helps even more

---

### Post by ales on 2006-06-09
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
212.55.250.0    0.0.0.0         255.255.255.0   U     0      0        0 eth1
dreamwalker@dreamwalker:~$
dreamwalker@dreamwalker:~$
 

seems that there is no gateway. should it be the ip of rouer or other IP? Why there is no gateway when it worked before....hmm

---

### Post by Slim Odds on 2006-06-09
[quote=ales]Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
212.55.250.0    0.0.0.0         255.255.255.0   U     0      0        0 eth1
dreamwalker@dreamwalker:~$
dreamwalker@dreamwalker:~$
 

seems that there is no gateway. should it be the ip of rouer or other IP? Why there is no gateway when it worked before....hmm[/quote]

Yes, you are missing a default route (which would point to the gateway address).

---

### Post by ales on 2006-06-09
[QUOTE=Slim Odds]Yes, you are missing a default route (which would point to the gateway address).[/QUOTE]



Ok and what should I do know. I tried to diable and activate the cards eth0 and 1 and it helped once. second tim not. Why? I don't know. Also in network settings u  can set the default gateway device eth0 or eth1 but ubuntu always changes it to none...

---

### Post by pnael on 2006-06-10
The default route adresse should be set by the dhcp client. It gets it from
the dhcp server with the ip address, netmask ... So usually this kind of
error is more a network configuration error.
You can check from a working configuration what should be the correct
ip configuration. Are you on a big network ? I mean you receive an public
ip address 212.55.250.18 from an dhcp server with a private ip address
10.0.0.138. It is not impossible but it is a "strange" setup.

If you know your default gateway ip address you can test it solves your
problem with the following command :
sudo route add default gw <default gw IP address>

---

### Post by ales on 2006-06-10
Well thanks to all problem solved but don§t know how. I edited ifconfig chcanged mac adresses of eth1aand 0. After that ubuntu saw only one device. so I disabled the one which was not in use an after it the internet works. Don§t know how but it works.

---

### Post by ales on 2006-06-10
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 eth0
dreamwalker@dreamwalker:~$

no w i got this 


My config is 1 router. Computer connecteed to router. To router is also connected Wifi acces point.

---

### Post by ales on 2006-06-18
Hmm now it is not working again. And reactivating eth has no effect. My router has IP 10.0.0.138 is it also IP of DHCP server, ehrn router is givimg IP to other devices?
I noticed, that in the network configuration there are two devices:
1. my eth whicg has Mask: 255.255.255.0
2. lo (loopback interface?) 255.0.0.0
Shouldn't be both the same?

I tried to boot the live cd and I noticed same problem with the network configuration. I I have already installed the Ubuntu, does the LiveCD use configuration files from disk?

THX Ales

---

### Post by bright_music on 2006-06-19
[QUOTE=pnael]The default route adresse should be set by the dhcp client. It gets it from
the dhcp server with the ip address, netmask ... So usually this kind of
error is more a network configuration error.
You can check from a working configuration what should be the correct
ip configuration. Are you on a big network ? I mean you receive an public
ip address 212.55.250.18 from an dhcp server with a private ip address
10.0.0.138. It is not impossible but it is a "strange" setup.

[/QUOTE]

Hello! More I read this more it looks I have the same problem... cant ping as well, and I am on big network, and network connections details are provided by dhcp client...still network unreachable! On the other hand it works just fine in win xp.

best!

---

### Post by Michel Tatoute on 2006-06-19
Same problem with different harware. I am on a kubuntu 6.06. 2 ethernet NIC  (one dhcp -> Internet, the other for my local network with masquerading).

with normal boot I got ifconfig ok (ip given..), route ok (except as i remember for the very first try, no default route) and DNS ok. But the interface (eth0) desesperately mute. tcpdump show no packet received at all even when the trafic on this network is not 0 (continuous flow of broadcast).

With mandiva on the same harware, no pb.

when i boot on single mode (recovery) the network works well. But launching starx mute it, and i found no mean to get it up again.

i try differents kernels, (2.6.15.23-386 , -686, 2.6.15.25-386, -686 & compile 2 directly from source of kernel.org (not sure, maybe  2.6.14.7 & 2.6.16.20)

i try boot options noacpi  & acpi=noirq ...

one time i got the network fine... but next reboot it vanishes...

strange problem.

Seems i am not alone in this case.

any help appreciated.
Michel.

---

### Post by ales on 2006-06-19
LOOK AT THIS. THIS IS IN MY /etc/network/interfaces


auto lo
iface lo inet loopback


iface eth0 inet dhcp (DISABLED IN BIOS)


auto eth2
iface eth2 inet dhcp  (WHAT IS THIS I DO NOT HAVE ETH2)

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp   I DO NOT HAVE W LAN CONNECTED TO PC WLAN IS CONNECTED TO ROUTER FOR MY LAPTOP





iface eth1 inet dhcp



auto eth1

auto eth0




SO THIS IS HOW MY FILE CONFIG FILE INTERFACES LOOKS LIKE. i HAVE 2 NETWORK CARDS MARVEL AND NVIDIA. NOW MARVEL (ETH0) IS DISABLED AND NVIDIA IS UP (IN UBUNTU ETH1). I THINK THIS FILE IS PRETTY WEIRD OR NOT?

---

### Post by goodmaj on 2006-06-20
I just helped a friend get wmp11 working in a Compaq desktop.  It runs just fine using ndiswrapper which can be obtained using Synaptic Package Manager.  The curcial step was to edit the file /etc/modprobe.d/ndiswrapper.  The file contains one line.

alias wlan0 ndiswrapper

For some reason this card insists that the line be

alias eth0 ndiswrapper

Change the wlan0 to eth0 and the card will then respond to 

ifup eth0

---

### Post by ales on 2006-06-20
[QUOTE=ales]dreamwalker@dreamwalker:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:D4:C2:28:FF
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:225 Base address:0x6000

eth1      Link encap:Ethernet  HWaddr 00:13:D4:C2:34:34
          inet addr:212.55.250.18  Bcast:212.55.250.255  Mask:255.255.255.0
          inet6 addr: fe80::213:d4ff:fec2:3434/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1820 (1.7 KiB)  TX bytes:1722 (1.6 KiB)
          Interrupt:58

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:272 (272.0 b)  TX bytes:272 (272.0 b)

dreamwalker@dreamwalker:~$
dreamwalker@dreamwalker:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
212.55.250.0    *               255.255.255.0   U     0      0        0 eth1
dreamwalker@dreamwalker:~$

 this is what i got[/QUOTE]


dreamwalker@dreamwalker:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:D4:C2:34:34
          inet addr:192.168.1.66  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:d4ff:fec2:3434/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:62075 errors:0 dropped:0 overruns:0 frame:0
          TX packets:62016 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:10510979 (10.0 MiB)  TX bytes:4761080 (4.5 MiB)
          Interrupt:66

eth1      Link encap:Ethernet  HWaddr 00:13:D4:C2:28:FF
          inet addr:212.55.249.25  Bcast:212.55.249.255  Mask:255.255.255.0
          inet6 addr: fe80::213:d4ff:fec2:28ff/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:45 errors:0 dropped:0 overruns:0 frame:0
          TX packets:39 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3763 (3.6 KiB)  TX bytes:4865 (4.7 KiB)
          Interrupt:50 Base address:0x8000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:811 errors:0 dropped:0 overruns:0 frame:0
          TX packets:811 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:23772 (23.2 KiB)  TX bytes:23772 (23.2 KiB)
 THIS IS WHEN IT WORKS

---

