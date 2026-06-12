---
title: "Wireless network only seen by router, not Firefox"
date: 2009-01-02
forum: Networking &amp; Wireless
---

### Post by oseney on 2009-01-02
Am having trouble with activating my laptop pcmcia card - Belkin fsd7011uk on Dell latitude ls. I have just installed xubuntu 8.04 . A new driver was available, B43, which I installed with its firmware. I had to tell it the network name (essid?) and it then connected to my router. Interrogating the router via another PC on its network confirmed this connection. However, on running Firefox, I found no internet connection and it would not even find the router on 192.168.1.1 . 

Is this Firefox's fault? BTW, when I use an ethernet cable connection direct to the router, the internet starts coming through immediately. This is how I'm sending this post.

[I previously installed ndiswrapper and used it to wrap the windows driver which came with the card. This worked too, found the router, but again not found by Firefox. This refers to my first installation of Xubuntu which I subsquently overlaid with a second installation having fouled up something. The other comments refer to this second installation (ndiswrapper is not installed this time). The B43 driver appears not to have been available first time round.]

 Here are the results of gnusci post (thread closed?) recommended terminal commands:
 
me3@me3-laptop:~$ lspci -nn | grep 'Wireless Brand'
me3@me3-laptop:~$ 
me3@me3-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
00:0a.0 CardBus bridge: Texas Instruments PCI1211
00:0d.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
00:10.0 Communication controller: Agere Systems WinModem 56k (rev 01)
01:00.0 VGA compatible controller: Neomagic Corporation NM2200 [MagicGraph 256AV] (rev 20)
01:00.1 Multimedia audio controller: Neomagic Corporation NM2200 [MagicMedia 256AV Audio] (rev 20)
02:00.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
me3@me3-laptop:~$ 

me3@me3-laptop:~$ lsusb | grep 'Wireless Brand'
me3@me3-laptop:~$ 

me3@me3-laptop:~$ lsusb
Bus 001 Device 001: ID 0000:0000  
me3@me3-laptop:~$ 

me3@me3-laptop:~$ iwconfig wlan0
wlan0     IEEE 802.11g  ESSID:"oseney isleland"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

me3@me3-laptop:~$ ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:11:50:f3:f3:6b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

me3@me3-laptop:~$ 

me3@me3-laptop:~$ lsmod | grep "wlan_module_name"
me3@me3-laptop:~$ 

me3@me3-laptop:~$ dmesg | grep "wlan_module_name"
me3@me3-laptop:~$ 

me3@me3-laptop:~$ sudo lshw -C network
[sudo] password for me3: 
  *-network               
       description: Ethernet interface
       product: 3c905C-TX/TX-M [Tornado]
       vendor: 3Com Corporation
       physical id: d
       bus info: pci@0000:00:0d.0
       logical name: eth0
       version: 78
       serial: 00:b0:d0:a4:09:a4
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=full ip=192.168.1.3 latency=80 link=yes maxlatency=10 mingnt=10 module=3c59x multicast=yes port=MII speed=100MB/s
  *-network
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:02:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:11:50:f3:f3:6b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
me3@me3-laptop:~$ 

me3@me3-laptop:~$ iwlist scan wlan0
iwlist: unknown command `wlan0' (check 'iwlist --help').
me3@me3-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

me3@me3-laptop:~$ 

me3@me3-laptop:~$ lsb_release -d
Description:	Ubuntu 8.04.1
me3@me3-laptop:~$ 

me3@me3-laptop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                             There is already a pid file /var/run/dhclient.wlan0.pid with pid 5268
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:11:50:f3:f3:6b
Sending on   LPF/wlan0/00:11:50:f3:f3:6b
Sending on   Socket/fallback
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:11:50:f3:f3:6b
Sending on   LPF/wlan0/00:11:50:f3:f3:6b
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
                                                            [ OK ]
me3@me3-laptop:~$

---

### Post by superprash2003 on 2009-01-02
try setting up static ip under preferences->network connections->wireless.. set ip to 192.168.1.10 and gateway to 192.168.1.1

---

### Post by oseney on 2009-01-02
> **superprash2003 said:**
> try setting up static ip under preferences->network connections->wireless.. set ip to 192.168.1.10 and gateway to 192.168.1.1

Thanks - but - my version of Firefox is 3.0.5 and has edit>preferences>advanced>network>settings with no options to insert your advised settings, only proxy setups. 
Am I looking in the right place?
btw - I have found that my router says the laptop is on the network even though I have deliberately given the wrong WEP password. This may be the problem - it's not really on the network at all and Firefox knows this. What do you think?

---

### Post by superprash2003 on 2009-01-03
no, im talking under system->admin->network .. this should help [http://www.prash-babu.com/2008/09/internet-works-on-one-pc-but-not-on_12.html](http://www.prash-babu.com/2008/09/internet-works-on-one-pc-but-not-on_12.html)

---

