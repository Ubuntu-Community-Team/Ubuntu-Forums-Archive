---
title: "wired network"
date: 2009-01-09
forum: Networking &amp; Wireless
---

### Post by skullomaniac on 2009-01-09
hey ppl
i have 2 ubuntu pc's
one is running 8.04 and the other one 8.10
on my 8.04 the wired network will work just fine but it has been configured by someone.. atleast the wireless connection has
on my 8.10 wired network doesn't work.. usually it should by default.. but my 8.10 pc hasn't been configured

i compared the two different results when typing ifconfig from the terminal

8.04 pc

> eth0      Link encap:Ethernet  HWaddr 00:c0:9f:a5:3f:ed  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:2219 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1921 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1994329 (1.9 MB)  TX bytes:295256 (288.3 KB)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 00:12:f0:9a:bb:b1  
          inet addr:10.0.0.104  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::212:f0ff:fe9a:bbb1/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:69432 errors:0 dropped:1 overruns:0 frame:0
          TX packets:4979 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Base address:0xe000 Memory:c820a000-c820afff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1582 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1582 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:81812 (79.8 KB)  TX bytes:81812 (79.8 KB)

8.10 pc

> eth0      Link encap:Ethernet  HWaddr 00:a0:d1:a0:49:2d  
          UP BROADCAST MULTICAST  MTU:64  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3201 (3.2 KB)  TX bytes:2889 (2.8 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:838 errors:0 dropped:0 overruns:0 frame:0
          TX packets:838 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:57184 (57.1 KB)  TX bytes:57184 (57.1 KB)


what do i do now???
thanks in advance!!

---

### Post by superprash2003 on 2009-01-09
try setting up static ip for the 8.10 machine..
For reference : [http://www.prash-babu.com/2009/01/how-to-setup-static-ip-in-ubuntu.html](http://www.prash-babu.com/2009/01/how-to-setup-static-ip-in-ubuntu.html)

---

### Post by skullomaniac on 2009-01-09
hey thanks for the reply but no, setting a static ip won't work...
could it be that my wired connection is not supposed to be eth0. maybe eth1???

i'm stuck.. don't know what to try now

---

### Post by albinootje on 2009-01-09
> **skullomaniac said:**
> hey thanks for the reply but no, setting a static ip won't work...
could it be that my wired connection is not supposed to be eth0. maybe eth1???

i'm stuck.. don't know what to try now

Please post the following :
```

ifconfig -a
lshw -C network
lspci
sudo dhclient

```

---

### Post by skullomaniac on 2009-01-12
this is what i got 

> eth0      Link encap:Ethernet  HWaddr 00:a0:d1:a0:49:2d  
          UP BROADCAST RUNNING MULTICAST  MTU:64  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2396 (2.3 KB)  TX bytes:3049 (3.0 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:486 errors:0 dropped:0 overruns:0 frame:0
          TX packets:486 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:30448 (30.4 KB)  TX bytes:30448 (30.4 KB)

pan0      Link encap:Ethernet  HWaddr fa:69:4a:8c:a6:b6  
          inet6 addr: fe80::f869:4aff:fe8c:a6b6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:2520 (2.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:18:de:d2:f2:73  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-18-DE-D2-F2-73-00-00-00-00-00-00-00-00-00-00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

  *-network               
       description: Ethernet interface
       product: 88E8055 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 12
       serial: 00:a0:d1:a0:49:2d
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 duplex=full firmware=N/A latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wmaster0
       version: 02
       serial: 00:18:de:d2:f2:73
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: fa:69:4a:8c:a6:b6
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GHM (ICH7-M DH) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 RAID bus controller: Intel Corporation 82801GHM (ICH7-M DH) SATA RAID Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300] (rev a1)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller (rev 12)
07:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
09:04.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
09:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
09:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
09:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
09:06.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
There is already a pid file /var/run/dhclient.pid with pid 6397
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
SIOCSIFFLAGS: No such device
SIOCSIFFLAGS: No such device
SIOCSIFFLAGS: Operation not supported
SIOCSIFFLAGS: Operation not supported
SIOCSIFADDR: No buffer space available
wmaster0: unknown hardware address type 801
Listening on LPF/pan0/fa:69:4a:8c:a6:b6
Sending on   LPF/pan0/fa:69:4a:8c:a6:b6
Listening on LPF/wlan0/00:18:de:d2:f2:73
Sending on   LPF/wlan0/00:18:de:d2:f2:73
Listening on LPF/wmaster0/
Sending on   LPF/wmaster0/
Listening on LPF/eth0/00:a0:d1:a0:49:2d
Sending on   LPF/eth0/00:a0:d1:a0:49:2d
Sending on   Socket/fallback
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 4
receive_packet failed on wlan0: Network is down
receive_packet failed on wmaster0: Network is down
DHCPREQUEST of 10.0.0.143 on eth0 to 255.255.255.255 port 67
send_packet: Message too long
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
send_packet: Network is down
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 5
send_packet: Network is down
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 7
DHCPREQUEST of 10.0.0.143 on eth0 to 255.255.255.255 port 67
send_packet: Message too long
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
send_packet: Network is down
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 14
send_packet: Network is down
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
send_packet: Network is down
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 15
send_packet: Network is down
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
send_packet: Message too long
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
send_packet: Message too long
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
send_packet: Network is down
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 16
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 20
send_packet: Message too long
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
send_packet: Network is down
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
send_packet: Network is down
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 11
send_packet: Network is down
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


---

### Post by albinootje on 2009-01-12
> **skullomaniac said:**
> 
DHCPREQUEST of 10.0.0.143 on eth0 to 255.255.255.255 port 67
send_packet: Message too long

Thanks!
Your network card is talking to the dhcp server, but..

Please check these :
[https://bugs.launchpad.net/ubuntu/+source/dhcp3/+bug/274069](https://bugs.launchpad.net/ubuntu/+source/dhcp3/+bug/274069)
[https://bugs.launchpad.net/ubuntu/+source/dhcp/+bug/294046](https://bugs.launchpad.net/ubuntu/+source/dhcp/+bug/294046)

---

### Post by skullomaniac on 2009-01-12
hey thx for the reply..
i followed the procedures, lowered the mtu and everything but still no luck..

---

### Post by albinootje on 2009-01-12
> **skullomaniac said:**
> hey thx for the reply..
i followed the procedures, lowered the mtu and everything but still no luck..

Did you remove the option interface-mtu in /etc/dhcp3/dhclient.conf and then ran dhclient again ?
IIRC that was one solution for someone earlier on a few weeks ago.

---

### Post by skullomaniac on 2009-01-12
yeah i did
it just says a bunch of time permission denied...

---

### Post by albinootje on 2009-01-12
> **skullomaniac said:**
> yeah i did
it just says a bunch of time permission denied...

OK, please try :
```

sudo dhclient eth0

```

---

### Post by skullomaniac on 2009-01-12
still no luck!! :(
it says something about line 21 in the dhclient.conf where i deleted interface-mtu

---

### Post by albinootje on 2009-01-12
> **skullomaniac said:**
> still no luck!! :(
it says something about line 21 in the dhclient.conf where i deleted interface-mtu

OK, mine looks like this, can you correct it ?
Perhaps you forgot the ";" in the end of those options.
If it's a "," sign, change it into the ";" after netbios-scope

```

# Configuration file for /sbin/dhclient, which is included in Debian's
#       dhcp3-client package.
#
# This is a sample configuration file for dhclient. See dhclient.conf's
#       man page for more information about the syntax of this file
#       and a more comprehensive list of the parameters understood by
#       dhclient.
#
# Normally, if the DHCP server provides reasonable information and does
#       not leave anything out (like the domain name, for example), then
#       few changes must be made to this file, if any.
#

send host-name "<hostname>";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, domain-name-servers, domain-search, host-name,
        netbios-name-servers, netbios-scope, interface-mtu;
#require subnet-mask, domain-name-servers;
#timeout 60;
#retry 60;
#reboot 10;
#select-timeout 5;
#initial-interval 2;
#script "/etc/dhcp3/dhclient-script";
#media "-link0 -link1 -link2", "link0 link1";
#reject 192.33.137.209;

```

---

### Post by skullomaniac on 2009-01-12
FINALLY!!
thanks for your help
i appreciate it

---

### Post by albinootje on 2009-01-12
> **skullomaniac said:**
> FINALLY!!
thanks for your help
i appreciate it

Good! Glad it's working :)

If you've changed any settings in Network Manager, then please try a reboot, and see whether it's still working, just to be sure.
If you didn't touch Network Manager settings at all, then it should be fine.

---

### Post by FudgeMutator on 2011-01-20
Thank you albino! I've been trying to figure this out for about 3 hours and this worked for me also.

Just to be clear on the fix for others looking at this:

1) I made my dhclient.conf look identical to what albino has posted above.
2) I typed "sudo dhclient eth0" in the terminal (without quotes)
3) I retried the connection and this time there was no issue

Thanks again,
-FudgeMutator

---

### Post by mathia on 2011-01-21
Hi,
please let me know which driver was in use on both systems:

$ sudo dmesg | grep sk

Thanks.

---

