---
title: "Wireless stoped working after trying to set up multi networks"
date: 2010-02-04
forum: Networking &amp; Wireless
---

### Post by Leeming on 2010-02-04
[Edit: Fixed] For people with same issue i can not give the exact solution to fix as some one at uni fixed it for me and we played around with a few things, in the end it came down to a faulty network manager

Originally I only used the wireless device on my laptop (eth1) which connects to the house wireless...
Decided to create a 2nd network (direct Ethernet between PC and laptop). Both networks exist on my PC and allow me to route to either the 10.x.x.x (direct/static) network and 192.168.1.x (wifi/dhcp) network. However on my laptop I managed to get both networks working, but then rebooted to check that configs where saved, since then my laptop's eth0 (ethernet) works but eth1 gives me a "No DHCPOFFERS" message when trying to restart networking (sudo /etc/init.d/networking restart).
I've even tried to stick a static IP in to access the wifi but that doesn't seem to work either, seems as tho the wifi is internally disabled (but can not find any thing to confirm this)

Additionally the network/wifi icon-menu says both wired & wireless are not managed.

Here is my laptop's /etc/network/interfaces
> auto lo
iface lo inet loopback


# The primary network interface
auto eth1
iface eth1 inet dhcp

auto eth0
iface eth0 inet static
address 10.0.0.11
netmask 255.255.255.0
gateway 10.0.0.10
network 10.0.0.0

ifconfig - eth1:avahi appeared when it stopped working
> 
eth0      Link encap:Ethernet  HWaddr 00:21:70:c6:0b:3e  
          inet addr:10.0.0.11  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::221:70ff:fec6:b3e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:747 errors:0 dropped:0 overruns:0 frame:0
          TX packets:883 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:261950 (261.9 KB)  TX bytes:250584 (250.5 KB)
          Interrupt:30 Base address:0x2000 

eth1      Link encap:Ethernet  HWaddr 00:23:4d:1a:52:48  
          inet6 addr: fe80::223:4dff:fe1a:5248/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 

eth1:avahi Link encap:Ethernet  HWaddr 00:23:4d:1a:52:48  
          inet addr:169.254.4.188  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1072 (1.0 KB)  TX bytes:1072 (1.0 KB)



results from /etc/init.d/networking restart
> 
leeming@lptLeeming:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth1.pid with pid 3196
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:23:4d:1a:52:48
Sending on   LPF/eth1/00:23:4d:1a:52:48
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 192.168.1.254 port 67
 * Reloading /etc/samba/smb.conf smbd only
   ...done.
RTNETLINK answers: No such process
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:23:4d:1a:52:48
Sending on   LPF/eth1/00:23:4d:1a:52:48
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
 * Reloading /etc/samba/smb.conf smbd only
   ...done.
                                                                         [ OK ]

Both laptop and PC are on 9.10

---

