---
title: "wireless network won't connect!"
date: 2009-03-26
forum: Networking &amp; Wireless
---

### Post by psyboy55 on 2009-03-26
When i go to system>admin>network click on my wireless and type everything in then i click ok nothing happens! it won't connect me to the internet! My driver is working Because my network connection applet can find other networks. The network app says im disconnected! i've retryed this many times but the system>admin>network app does nothing. Is there an alternative wifi tool?

---

### Post by Cheesehead on 2009-03-26
Open a terminal and try the following commands. Paste the results of each to the thread.
(note: replace 'eth1' with your interface's name, and your_network with your ESSID, of course)
```

1) $sudo iwconfig eth1 essid your_network

2) $sudo dhclient3 eth1

```

---

### Post by sgosnell on 2009-03-26
Have you tried just clicking on the network icon in your panel, and seeing if your network shows up?  Is your router broadcasting the SSID?  If not, you can select Connect to hidden wireless network, and give the resulting dialog the pertinent information.

---

### Post by psyboy55 on 2009-03-26
the first piece of code didn't work (nothing happened) but the second one did
i got:

Internet Systems Consortium DHCP client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:1d:60:06:9c:22
Sending on   LPF/eth1/00:1d:60:06:9c:22
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by sgosnell on 2009-03-26
eth1 is an ethernet port, not a wireless port.  That was given as a placeholder.  You need to use your wireless port, probably ath0.

---

### Post by psyboy55 on 2009-03-26
it's not ath0. how do i find out what it is? I plugged my wireless into the same slot i did my ethernet (i removed the ethernet card)

---

### Post by sidewinder12s on 2009-03-26
Well i have the same problem, where When i put in the Password for the network it just kicks me out and tells me to enter the Pass over and over.
Hope its the same Problem

I ran the Code 

```
1) $sudo iwconfig eth1 essid your_network
```
And it did nothing, I changed all the Placeholders right and it did nothing. just went to a new Command

For
```
2) $sudo dhclient3 eth1
```
I got
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:0d:3a:6e:8b:00
Sending on   LPF/wlan0/00:0d:3a:6e:8b:00
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

Any help would be Great

---

### Post by psyboy55 on 2009-03-26
it's kind of the same problem. How did you find out your wireless port? i thought it was eth1 but i guess it isn't.

---

### Post by sidewinder12s on 2009-03-26
Mine was wlan0, its under Network Devices in The Devices tab.

I kinda guessed which one was the Wireless card from that list

---

### Post by psyboy55 on 2009-03-26
it's not wlan0. Where is the devices tab? i found restricted drivers but not devices.

---

### Post by sidewinder12s on 2009-03-26
Under system-Admin-Network Tools. I already have the Driver for my card working

restricted

---

### Post by fieroboom on 2009-03-27
> **sgosnell said:**
> eth1 is an ethernet port, not a wireless port.  That was given as a placeholder.  You need to use your wireless port, probably ath0.

The logical name eth1 is perfectly acceptable as a wireless interface. My Broadcom BCM4306 uses eth1 as well.

> **psyboy55 said:**
> it's kind of the same problem. How did you find out your wireless port? i thought it was eth1 but i guess it isn't.

Please run these two commands, and copy/paste the results here.
```
ifconfig -a

sudo lshw -C network
```
:D
-Paul

---

### Post by sidewinder12s on 2009-03-27
geoff@geoff-laptop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:0d:56:ae:3b:01  
          inet addr:192.168.1.68  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:56ff:feae:3b01/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1504293 errors:0 dropped:0 overruns:0 frame:0
          TX packets:979274 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2245680734 (2.2 GB)  TX bytes:74016427 (74.0 MB)
          Interrupt:7 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:131221 errors:0 dropped:0 overruns:0 frame:0
          TX packets:131221 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6598273 (6.5 MB)  TX bytes:6598273 (6.5 MB)

pan0      Link encap:Ethernet  HWaddr fe:3a:10:b7:da:b1  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:0d:3a:6e:8b:00  
          inet6 addr: fe80::20d:3aff:fe6e:8b00/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:60 (60.0 B)  TX bytes:9936 (9.9 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-0D-3A-6E-8B-00-62-30-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

geoff@geoff-laptop:~$ 
geoff@geoff-laptop:~$ sudo lshw -C network
[sudo] password for geoff: 
  *-network               
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 01
       serial: 00:0d:56:ae:3b:01
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.1.68 latency=32 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: 802.11b CardBus
       vendor: Broadcom
       physical id: 0
       version: 8.0
       slot: Socket 0
       resources: irq:11
  *-network
       description: Network controller
       product: BCM43xG 802.11b/g
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:03:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: fe:3a:10:b7:da:b1
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
  *-network:1
       description: Wireless interface
       physical id: 3
       logical name: wlan0
       serial: 00:0d:3a:6e:8b:00
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

---

### Post by fieroboom on 2009-03-27
Ok, you've got a Broadcom chipset. Run this command and post the results.
```
lspci | grep Broadcom
```
Or, if you want to skip my step-by-step, follow [this guide](http://ubuntuforums.org/showthread.php?t=185174)
:D
-Paul

EDIT
Note that when you upgrade your kernel, you'll need to recompile this driver. On 90% of the older Broadcoms I've used (and I have a lot of them), the fwcutter method works more reliably than any of the 'newer' drivers, such as the B43.

---

### Post by sidewinder12s on 2009-03-27
geoff@geoff-laptop:~$ lspci | grep Broadcom
02:01.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
03:00.0 Network controller: Broadcom Corporation BCM43xG 802.11b/g (rev 02)

---

### Post by psyboy55 on 2009-03-27
ok here it is

eth0      Link encap:Ethernet  HWaddr 00:20:18:DC:15:1E  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b) 
          Interrupt:9 Base address:0xe000 

eth1      Link encap:Ethernet  HWaddr 00:1D:60:06:9C:22  
          inet6 addr: fe80::21d:60ff:fe06:9c22/64 Scope:Link 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:153 errors:0 dropped:9257 overruns:0 frame:0 
          TX packets:67 errors:0 dropped:1854 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:19681 (19.2 KB)  TX bytes:2914 (2.8 KB) 
          Interrupt:255 Base address:0x8000 

eth1:avah Link encap:Ethernet  HWaddr 00:1D:60:06:9C:22  
          inet addr:169.254.4.10  Bcast:169.254.255.255  Mask:255.255.0.0 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          Interrupt:255 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:627 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:627 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:57662 (56.3 KB)  TX bytes:57662 (56.3 KB) 


Second one...


Hardware Lister (lshw) - B.02.10 
usage: lshw [-format] [-options ...] 
       lshw -version 

        -version        print program version (B.02.10) 
 
format can be 
        -html           output hardware tree as HTML 
        -xml            output hardware tree as XML 
        -short          output hardware paths 
        -businfo        output bus information 

options can be 
        -class CLASS    only show a certain class of hardware 
        -C CLASS        same as '-class CLASS' 
        -disable TEST   disable a test (like pci, isapnp, cpuid, etc. ) 
        -enable TEST    enable a test (like pci, isapnp, cpuid, etc. ) 
        -quiet          don't display status 

david@ubuntu:~$ sudo 1shw -c network 
sudo: 1shw: command not found 
david@ubuntu:~$ sudo lshw -C network 
  *-network:0             
       description: Ethernet interface 
       product: RTL-8139/8139C/8139C+ 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: 9 
       bus info: pci@0000:01:09.0 
       logical name: eth0 
       version: 10 
       serial: 00:20:18:dc:15:1e 
       size: 10MB/s 
       capacity: 100MB/s 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s 
  *-network:1 
       description: Wireless interface 
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller 
       vendor: Broadcom Corporation 
       physical id: a 
       bus info: pci@0000:01:0a.0 
       logical name: eth1 
       version: 02 
       serial: 00:1d:60:06:9c:22 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master ethernet physical wireless 
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.22-16-generic latency=64 link=yes module=bcm43xx multicast=yes wireless=IEEE 802.11b/g

---

### Post by TBerk on 2009-03-27
I have a similar problem; I can DHCP just fine when i plug in the cable into the built in ethernet, but while I as fine with my wireless just fine a few days ago, I have narrowed it down now to the following:

- I can boot OK but wicd no longer will handle a connect to the router. (I had changed no settings.)

- If I open a terminal window and enter ```
$sudo dhclient3 ra0
``` I get a green confirmation in the wicd applet and my network connect via DHCP is up and running.

I have included the two bits of requested info listed up-thread a ways:

```
$iwconfig
```

lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT2860 Wireless  ESSID:"polycarbonate"  Nickname:"RT2860STA"
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:16:B6:B2:FD:20   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:-56 dBm  Noise level:-71 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



```
$ sudo dhclient3 ra0
```

There is already a pid file /var/run/dhclient.pid with pid 6395
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/ra0/00:1d:6a:20:6a:eb
Sending on   LPF/ra0/00:1d:6a:20:6a:eb
Sending on   Socket/fallback
DHCPREQUEST of 192.168.1.101 on ra0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.101 from 192.168.1.2
bound to 192.168.1.101 -- renewal in 37765 seconds.


TBerk
(now all I have to do is find out how to get rid of the smileys)

---

### Post by matsr on 2009-05-01
> **Cheesehead said:**
> Open a terminal and try the following commands. Paste the results of each to the thread.
(note: replace 'eth1' with your interface's name, and your_network with your ESSID, of course)
```

1) $sudo iwconfig eth1 essid your_network

2) $sudo dhclient3 eth1

```


I had somewhat the same problem on my HP nc2400, using iwl3945 drivers for my wireless nic and ubuntu 9.04. modifing Cheesehead's suggesting i managed to get this working with the following commands:
```

1) sudo iwconfig wlan0 essid [ssid of network]

2) sudo dhclient wlan0

```
notice only the 3 is missing from the second command, I don't know why but dhclient3 didn't work for me

EDIT:
btw: I think you can see the name of your wireless nic by typing: "sudo iwconfig" in your terminal(without quotes). it will list your nics and tell you which of them that does not have wireless extensions.

---

### Post by coutts99 on 2009-05-01
> **sgosnell said:**
> eth1 is an ethernet port, not a wireless port.  That was given as a placeholder.  You need to use your wireless port, probably ath0.


Incorrect info here, eth1 is perfectly fine for a wireless card

---

