---
title: "DSL ethernet fail"
date: 2009-04-03
forum: Networking &amp; Wireless
---

### Post by hcbmbr on 2009-04-03
Hello. I am trying to setup Ubuntu Hoary on my IBM Thinkpad T40. But, I am unable to get the DSL ethernet connection up and running.

I have looked through many threads trying to solve the problem, but have been unable. Here is where I stand:

The ethernet card is an Intel 82801DB Pro/100 VE (MOB). I entered all the correct IP addresses into the Network Configuration "Wired" windows, listed under the "IPv4" settings.

When I get to the main desktop of Ubuntu a window pops up telling me that I am connected via eth0, but when I open up Firefox no URLs respond. 

When I run "sudo pppoeconf" I get 4 ethernet ports, but the tests come up nil on all of them.

Below are copies of commands I entered to gather information; these were taken from other threads, but I have no idea what any of this means.

Any help you could give would be GREATLY appreciated. Thank you.



hcb@ubuntu:~$ ifconfig -a

eth0      Link encap:Ethernet  HWaddr 00:0d:60:5e:af:ee  
          inet addr:12.148.234.235  Bcast:12.148.235.255  Mask:255.255.252.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:3109 (3.1 KB)

irda0     Link encap:IrLAP  HWaddr 00:00:00:00  
          NOARP  MTU:2048  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:8 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:254 errors:0 dropped:0 overruns:0 frame:0
          TX packets:254 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:16000 (16.0 KB)  TX bytes:16000 (16.0 KB)

pan0      Link encap:Ethernet  HWaddr fa:18:a6:32:75:62  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


hcb@ubuntu:~$ sudo dhclient

[sudo] password for hcb: 
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/pan0/fa:18:a6:32:75:62
Sending on   LPF/pan0/fa:18:a6:32:75:62
Listening on LPF/eth0/00:0d:60:5e:af:ee
Sending on   LPF/eth0/00:0d:60:5e:af:ee
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


hcb@ubuntu:~$ dhclient eth0

There is already a pid file /var/run/dhclient.pid with pid 5928
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

can't create /var/lib/dhcp3/dhclient.leases: Permission denied
SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFFLAGS: Permission denied
Open a socket for LPF: Operation not permitted

---

