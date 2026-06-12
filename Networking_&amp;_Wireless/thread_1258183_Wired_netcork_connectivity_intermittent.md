---
title: "Wired netcork connectivity intermittent"
date: 2009-09-04
forum: Networking &amp; Wireless
---

### Post by vaadoo on 2009-09-04
I used to have no problems with having a stable internet connection until kernel upgrade (I think I am using the right terminology).
Now, if I configure the eth0 to DHCP, the internet works fine for a couple of days and then it stops working and I can't browse to any website. I have attached a local printer to this machine which is also accessible over the network from other computers and I can't print anything because the network connectivity is lost. then what I have to do is either change from DHCP to static IP address or vice versa and it comes back online again. I have also tried /etc/init.d/networking restart command and that works also.
Any suggestions as to why this is not a permamanent solution? What files/upgrade do I need to achieve.
here's the output of ifconfig:
eth0 Link encap:Ethernet HWaddr 00:60:08:2b:4c:84
inet addr:192.168.0.106 Bcast:192.168.0.255 Mask:255.255.255.0
inet6 addr: fe80::260:8ff:fe2b:4c84/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:230383 errors:0 dropped:0 overruns:0 frame:0
TX packets:47900 errors:0 dropped:0 overruns:0 carrier:9
collisions:4878 txqueuelen:1000
RX bytes:109588235 (104.5 MB) TX bytes:10419914 (9.9 MB)
Interrupt:11 Base address:0xb800

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:6992 errors:0 dropped:0 overruns:0 frame:0
TX packets:6992 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:395142 (385.8 KB) TX bytes:395142 (385.8 KB)

Here are the contents of /etc/resolv.conf

nameserver 192.168.0.1


and finally
/$ cat /etc/network/interfaces
auto lo
iface lo inet loopback




auto eth0
iface eth0 inet dhcp


------
1. This desktop is connected with ethernet connection to the router. And its automatic DHCP & DNS servers.
2, I may have assigned the 192.168.0.72 manually when the DHCP config was giving me connectivity problems. I don't know how to fix these files to reflect identical IP addresses.
3. nameserver provides DNS. I have 2 other pc laptops that connect to this router wirelessly and they don't have any problem with connectivity.
4. Output from route -n

Kernel IP routing table
Destination Gateway Genmask Flags Metric Ref Use Iface
192.168.0.0 0.0.0.0 255.255.255.0 U 0 0 0 eth0
169.254.0.0 0.0.0.0 255.255.0.0 U 1000 0 0 eth0
0.0.0.0 192.168.0.1 0.0.0.0 UG 100 0 0 eth0



is there a timeout setting for renewal that needs to be reset?

The internet went down (I believe when the system came up from a sleep mode).
When I ran the following command, I got some error messages below.

I had to resort my work around way of assigning a static ip address.

Please have a look at networking restart command and its output.

/$ sudo /etc/init.d/networking restart
[sudo] password for glore:
* Reconfiguring network interfaces... There is already a pid file /var/run/dhclient.eth0.pid with pid 16830
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:60:08:2b:4c:84
Sending on LPF/eth0/00:60:08:2b:4c:84
Sending on Socket/fallback
DHCPRELEASE on eth0 to 192.168.0.1 port 67
There is already a pid file /var/run/dhclient.eth0.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:60:08:2b:4c:84
Sending on LPF/eth0/00:60:08:2b:4c:84
Sending on Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

----
I have upgraded to Ubuntu 9.04 but am still faced with the same problem.
Is there Anyone out there who understands my situation?


I have also now installed Wicd Network manager, but haven't verified if it has made any difference.

Many thanks!!!

Vaadoo

---

