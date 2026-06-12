---
title: "Wireless network enabled ..browser and other network stuffs not working.."
date: 2010-02-04
forum: Networking &amp; Wireless
---

### Post by rahulvom on 2010-02-04
hello there somebdy jus help me fix this...i hav ubuntu 9.10 installed in my laptop...and we have a wireless network running..the problem is that it displays wireless network connected....but my browser and other stuffs like software package management that needs internet are not working..should i make adjustments to network connections....if it is the case what should i suffice to make my browser run....please be fast. .. Even ping tells unknown host google.com.......

---

### Post by adam814 on 2010-02-04
Post the outputs of these commands in the terminal:

1) "ifconfig"
2) "iwconfig"
3) "route -n"
4) "sudo lshw -C network"

---

### Post by rahulvom on 2010-02-06
actionparsnip requested for more information:
Can you give the output of:

sudo lshw -C network;
output:
  *-network description: 
Wireless interface
 product: PRO/Wireless 3945ABG [Golan] Network Connection
 vendor: Intel Corporation physical id: 0
 bus info: pci@0000:03:00.0
 
logical name: wmaster0   version: 02  serial: 00:1b:77:08:bb:f2 width: 32 bits clock: 33MHz
 capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless configuration: broadcast=yes driver=iwl3945 ip=192.168.1.5 latency=0 multicast=yes wireless=IEEE 802.11abg
   resources: irq:26 memory:d0000000-d0000fff
  

*-network
       description: Ethernet interface
 product: RTL-8139/8139C/8139C+
 vendor: Realtek Semiconductor Co., Ltd.
 physical id: 1
bus info: pci@0000:05:01.0
 logical name: eth0
 version: 10 serial: 00:0f:b0:d1:aa:97
 size: 10MB/s
 capacity: 100MB/s width: 32 bits
  clock: 33MHz
  capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
       resources: irq:21 ioport:2000(size=256) memory:d0100000-d01000ff





ifconfig;
Output:
rahul@rahul-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0f:b0:d1:aa:97  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:21 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1b:77:08:bb:f2  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:77ff:fe08:bbf2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:210 errors:0 dropped:0 overruns:0 frame:0
          TX packets:146 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:32755 (32.7 KB)  TX bytes:18999 (18.9 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1B-77-08-BB-F2-30-38-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000   RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
 

route;
Output:
rahul@rahul-laptop:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     2      0        0 wlan0
link-local      *               255.255.0.0     U     1000   0        0 wlan0
default         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0


 ping [www.google.com](www.google.com) -c 1;
Output:
rahul@rahul-laptop:~$  ping [www.google.com](www.google.com) -c 1
ping: unknown host [www.google.com](www.google.com)

 ping 216.239.59.104 -c 1
Output:
rahul@rahul-laptop:~$  ping 216.239.59.104 -c 1
PING 216.239.59.104 (216.239.59.104) 56(84) bytes of data.
64 bytes from 216.239.59.104: icmp_seq=1 ttl=52 time=391 ms

--- 216.239.59.104 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms rtt min/avg/max/mdev = 391.132/391.132/391.132/0.000 ms





please be fast....

---

### Post by adam814 on 2010-02-06
Looks like somewhere along the way your DNS isn't working.

What do you get if you try "nslookup google.com"?

The easiest thing to do would be to right-click the NetworkManager icon on your menu bar, choose Edit Connections, then the connection for your network and click Edit.

Go to IPv4 Settings and change it from Automatic (DHCP) to Automatic (DHCP) addresses only.  Add your ISP DNS server addresses to the field for it.  If you don't have those handy you could also use OpenDNS or GoogleDNS (8.8.8.8 ).

That will at least get you back online while you figure out what's going on if you don't find it an acceptable long-term fix.

---

### Post by espressobeanie on 2010-02-06
Or maybe it's the router. Type 192.168.1.1 in the firefox browser. See if that works. Then, try plugging the laptop into the router and see if it works.

---

### Post by crlang13 on 2010-02-06
Hey,

I'm a total newbie, so this might not help (nowhere near as technical as the guy above).  Does your network need a proxy to run through (most likely if you're running through a work or school network)?  Because if it does, you can be "connected," but won't be able to use most internet services.

For example, my university's network requires me to run through their proxy in order to view any web pages other than theirs.  I can put the proxy configurations into firefox (edit => preferences => advance => network => settings).  You can configure the proxy in there, or, tick "use system settings" and configure the proxy in whatever network proxy manager you use and apply it system wide.  This is better because then you can use all your internet applications through the network.

Might not be the solution, but may be the obvious one that works!

---

