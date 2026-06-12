---
title: "Ubuntu 8.10 fails to detect wired network"
date: 2009-03-09
forum: Networking &amp; Wireless
---

### Post by vijayakumarpl on 2009-03-09
I have installed Ubuntu 8.1.0 and every thing went well for a week. I had set up  Systes->preferences->power management "put computer to sleep" option All of a sudden when waking up from sleep, wired network stopped working 

nm-tool output


NetworkManager Tool

State: connected

- Device: eth0 ----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             unmanaged
  Default:           no
  HW Address:        00:00:00:00:00:00

  Capabilities:
    Supported:       yes
    Carrier Detect:  yes

  Wired Settings


ifconfig -a output

eth0      Link encap:Ethernet  HWaddr 00:1a:a0:92:24:34  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:fdfc0000-fdfe0000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

pan0      Link encap:Ethernet  HWaddr f6:39:54:06:8d:14  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



/etc/network/interfaces content

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

[ifupdown]
managed=true


In the syslog, it talks about 
[http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889)


Is there a workaround for the above problem.

I know the network card is good, since i dual boot on the box. I issued a command to check the carrier and it returned a value of 0.

---

### Post by Crafty Kisses on 2009-03-09
What are the results of this command?
```
lspci | grep Ethernet
```

---

### Post by vijayakumarpl on 2009-03-10
Output of lspci | grep Ethernet


00:19.0 Ethernet controller: Intel Corporation 82562V-2 10/100 Network Connection (rev 02)

---

### Post by Janus23 on 2009-04-07
I am having similar problems, with similar outputs.  I upgraded to 8.10 about two weeks ago.  Everything was working fine until yesterday, when wired connection under NM showed device not managed.  Yesterday, wireless showed available networks.  Now however, both wired and wireless show unmanaged. Can someone help me.  I am not so new to Ubuntu, but not so skilled either.  Thanks. . .

---

### Post by Janus23 on 2009-04-07
ok, so I tried this:  [https://answers.launchpad.net/ubuntu/+question/58626](https://answers.launchpad.net/ubuntu/+question/58626)

and changed managed=true in /etc/NetworkManager/nm-system-settings.conf

this worked, but only for the wireless.  thanks to nhasian!!!  Now can anyone tell me how to fix the wired?  In network manager, my wired connection is now called ifupdown (eth0).

Dell Inspiron 1420n, Ibex, kernal 2.6.27-14-generic

This it the output for dhclient eth0:
There is already a pid file /var/run/dhclient.pid with pid 8628
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth0/00:1e:c9:08:a8:66
Sending on   LPF/eth0/00:1e:c9:08:a8:66
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

This is the output for ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:1e:c9:08:a8:66  
          inet6 addr: fe80::21e:c9ff:fe08:a866/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1131 (1.1 KB)  TX bytes:1184 (1.1 KB)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:1f:3c:7d:0c:57  
          inet addr:192.168.100.13  Bcast:192.168.100.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:3cff:fe7d:c57/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9543 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7908 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10326193 (10.3 MB)  TX bytes:1136500 (1.1 MB)

eth0:avahi Link encap:Ethernet  HWaddr 00:1e:c9:08:a8:66  
          inet addr:169.254.6.103  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200 (200.0 B)  TX bytes:200 (200.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-1F-3C-7D-0C-57-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

and  lspci | grep Ethernet:

09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)

---

