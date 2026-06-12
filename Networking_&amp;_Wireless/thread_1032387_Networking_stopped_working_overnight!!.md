---
title: "Networking stopped working overnight!!"
date: 2009-01-06
forum: Networking &amp; Wireless
---

### Post by systat on 2009-01-06
Last night my WLAN worked, everything was perfect, and today when I woke up, and turn on laptop, I keep getting message no connection, even though, I could see my WLAN network, on list, and it's signal was fine.

I tried couple of times to connect, and the connecting icon was only showing lower blinking green light, while there was no blinking on upper green light.
And after couple of blinks,I get no network connection.


When I try to join WLAN, message on icon is Attempting to Join wireless network 'SpeedTouchDC3987'.
And after some time, icon change to, no network connection.

I tried to connect to wired network, because I knew that worked every time when I installed Ubuntu, and needed to download necessary files to setup WLAN, but there same problem.

Requesting Network Address from Wired netwok message.
That message was there for 5 minutes, and tehre was connecting icon, lower green light was blinking, and so I decided to quit, I connected network cable back to my Windows XP desktop computer, and write this.

WLAN also works on my other laptop that is powered by Windows XP, so there must be some problem with my laptop





laptop@vampire:~$ sudo dhclient
[sudo] password for laptop:
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFFLAGS: Permission denied
Listening on LPF/wlan1/00:1a:73:6c:4c:b6
Sending on LPF/wlan1/00:1a:73:6c:4c:b6
Listening on LPF/eth0/00:1a:4b:5e:2e:fe
Sending on LPF/eth0/00:1a:4b:5e:2e:fe
Sending on Socket/fallback
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
laptop@vampire:~$



laptop@vampire:~$ ifconfig
eth0 Link encap:Ethernet HWaddr 00:1a:4b:5e:2e:fe
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:44 errors:0 dropped:0 overruns:0 frame:0
TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:4382 (4.2 KB) TX bytes:3060 (2.9 KB)
Interrupt:17

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:292 errors:0 dropped:0 overruns:0 frame:0
TX packets:292 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:14600 (14.2 KB) TX bytes:14600 (14.2 KB)

wlan1 Link encap:Ethernet HWaddr 00:1a:73:6c:4c:b6
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:70 errors:0 dropped:0 overruns:0 frame:0
TX packets:50 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:5797 (5.6 KB) TX bytes:8148 (7.9 KB)
Interrupt:18 Memory:c8000000-c8004000


laptop@vampire:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by superprash2003 on 2009-01-06
which ubntu version are you running?? have you tried static ip?? post outpt of 
1)iwlist scanning
2)lshw -C network

---

### Post by tuxxy on 2009-01-06
Try pressing the wireless button on router first then retry.

---

### Post by systat on 2009-01-06
@tuxy what I tried everything. It is not a ROUTER problem, because I can to WLAN connect fine using Windows XP laptop.
and about what button are you talking?
I was writing about this green lamp
Only lower is green, and I know that upper is suppose to respond, but it doesnt.
[http://imagebin.ca/view/hLewAr.html](http://imagebin.ca/view/hLewAr.html)

@superprash

I use Ubuntu 8.04.

I don't know about static IP, my default configuration worked until this morning, for 3 months.
laptop@vampire:~$ lshw -C network
WARNING: you should run this program as super-user.
PCI (sysfs)  
laptop@vampire:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       logical name: eth0
       version: 02
       serial: 00:1a:4b:5e:2e:fe
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 duplex=full latency=0 link=no module=tg3 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:30:00.0
       logical name: wlan1
       version: 02
       serial: 00:1a:73:6c:4c:b6
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,10/12/2006, 4.100. latency=0 link=no module=ndiswrapper multicast=yes wireless=IEEE 802.11g


laptop@vampire:~$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan1     Scan completed :
          Cell 01 - Address: 00:90:D0:F6:1B:13
                    ESSID:"SpeedTouchDC309B"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:100/100  Signal level:-32 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

---

### Post by systat on 2009-01-07
Guess no one knows, damn, I guess I need switch back to windows then.

---

### Post by superprash2003 on 2009-01-07
try this [http://www.prash-babu.com/2008/10/wifi-tip-always-better-to-disable.html](http://www.prash-babu.com/2008/10/wifi-tip-always-better-to-disable.html) .. if DHCP doesnt work.. use Static ip.. if you router ip is 192.168.1.1 then set static ip to 192.168.1.10 and gateway as 192.168.1.1 .. if router ip is 192.168.0.1 then set static ip to 192.168.0.10 and gateway as 192.168.0.1

---

