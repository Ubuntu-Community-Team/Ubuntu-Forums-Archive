---
title: "very slow internet on ubuntu 10.10 amd 64"
date: 2011-01-21
forum: Networking &amp; Wireless
---

### Post by the ruler on 2011-01-21
Hey,

I have superslow internet that stops working the whole the time. With windows  7 and pclinuxos I had a stable connection and I could download on +-1MB per second.

The router is located 2 floors down, so it is normal that the connection isn't superfast, but waiting half an hour on a page isn't normal anymore. I have a hercules wireless pci card for wifi (802.11n) and the router is from usrobotics (type: usr5464 and with broadcom software)

I foud this solution somewhere:

[I]sudo gedit /etc/modprobe.d/blacklist.conf

Add the following lines to the end of blacklist.conf:[/I] [I]

blacklist rt2800pci[/I] [I]
blacklist rt2800usb
blacklist rt2x00lib
blacklist rt2x00pci
blacklist rt2x00usb [/I]

This helped to get a speed of 300kbps , until I installed tinyproxy for my XBMC. I uninstalled tinyproxy via synaptic because I got the slow speed again but the speed remained low and faded away the whole time. With low speed I mean around 10 bytes (not kb :s) per second.

Does anyone have an idea to solve this, because my internetconnection is kind of essential..

Regards, the ruler.

PS: I see that I marked this as a kubuntu problem, but it is an ubuntu problem ;)

---

### Post by gordintoronto on 2011-01-21
It's possible this will help: (from the January Full Circle Magazine)

Start Firefox, then type into the address: 
about:config 
Ignore the warning which comes up. Type into the filter box: ipv6. Double-click the line to change the value from false to true. Restart Firefox for full-speed browsing.

---

### Post by the ruler on 2011-01-22
I applied the fix above, and my speed is better, but my speed was also better today before that I applied the fix. So I don't know if it's permanently fixed or that I'm just lucky today. To be certain I looked up all the info I could get:


_iwconfig_

eth0      no wireless extensions.

wlan0     Ralink STA  ESSID:"USR5464"  Nickname:"RT2860STA"
          Mode:Managed  Frequency=2.412 GHz  Access Point: 00:14:C1:26:BB:B4   
          Bit Rate=2 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=35/100  Signal level:-84 dBm  Noise level:-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

_ifconfig_

eth0      Link encap:Ethernet  HWaddr 00:21:85:1c:8d:7f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:43 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:08:d3:50:08:95  
          inet addr:192.168.2.3  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::208:d3ff:fe50:895/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:101995 errors:0 dropped:0 overruns:0 frame:0
          TX packets:60379 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:132152577 (132.1 MB)  TX bytes:6630430 (6.6 MB)
          Interrupt:20 
[U]
lshw | head[/U]

description: Desktop Computer
    product: MS-7501
    vendor: MEDIONPC
    version: 2.1
    serial: To Be Filled By O.E.M.
    width: 64 bits
    capabilities: smbios-2.5 dmi-2.5 vsyscall64 vsyscall32
    configuration: chassis=desktop uuid=C8D2CF35-5E68-DD11-85F6-D9CC04B6A3EC
  *-core

_lshw -c Network:_

 
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:21:85:1c:8d:7f
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:43 ioport:e800(size=256) memory:fe9ff000-fe9fffff memory:fdff0000-fdffffff memory:fe9c0000-fe9dffff
  *-network
       description: Wireless interface
       product: RT2800 802.11n PCI
       vendor: RaLink
       physical id: 2
       bus info: pci@0000:05:02.0
       logical name: wlan0
       version: 00
       serial: 00:08:d3:50:08:95
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2860 ip=192.168.2.3 latency=64 maxlatency=4 mingnt=2 multicast=yes wireless=Ralink STA
       resources: irq:20 memory:febf0000-febfffff

Does all this looks normal?? ;)

---

### Post by dineshs on 2011-01-22
If there is a delay in loading pages you may 
1)disable ipv6 as gordintoronto suggested.
2)Try a different  DNS such as 4.2.2.1 or 8.8.8.8 or 8.8.4.4
3)Change MTU  (At present the setting is 1500 .You may try 1492 or 1482)The settings can be changed via network manager .You may have to reboot or run ```
sudo service network-manager restart
```
Note :[This]("http://ubuntuforums.org/showthread.php?t=872346") guide may help you findout optimum MTU value

---

### Post by the ruler on 2011-01-24
Thanks for the help, but it was something else that caused my problem.

I tried some things with libstdc++5, wireless Backports-modules, and ndiswrapper and the problem is solved now! I downloaded UrbanTerror against 1.8MBps and played it flawless online :)

---

