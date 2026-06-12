---
title: "wireless won't connect"
date: 2011-11-09
forum: Networking &amp; Wireless
---

### Post by ssolari on 2011-11-09
Hello-- I'm new to the Ubuntu world and this list, so please forgive my neophyte-ness.  
I just successfully installed 11.10 on a Acer TravelMate C100, but for some reason, although it finds the signals, the wireless won't connect to any of them. With my particular network, it asks for my key, which I enter, but it still will not connect. I also tried a different, open network and plugging the LAN line in, but nothing. If I boot up the old OS (Windows XP) the wireless works fine.
Any advice on how to resolve this would be greatly appreciated.

---

### Post by josephmills on 2011-11-09
Hi there Hope that you are figuring it out. there is a sticky thread  at the top of this forum it is something like how to fill out a wireless ticket. I suggest that you look at that then give us some more information on your wireless card and what you are seeing when enter the commands from that thread thanks here is a link to that thread [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108) 
Have a great day !

---

### Post by ssolari on 2011-11-09
Sorry about that. Here is the information requested in the sticky post:
1) Machine: Acer TravelMate C100 laptop
2) Wireless: ORiNOCO Mini PCI Card (Lucent Technologies) on Texas Instruments PCI1410 PC CardBus Controller (see below)
3) Interface: see below
4) Modules: see below
5) Kernel boot messages: see below
6) Network configuration: see below
7) Scan for networks: see below
8) Ubuntu version: Ubuntu 11.10
9) Kernel/architecture: 3.0.0-12-generic i686
10) Restarting the network: see below


ssolari@ssolari-TravelMate-C100:~$ lspci
00:00.0 Host bridge: Intel Corporation 82440MX Host Bridge (rev 01)
00:00.1 Multimedia audio controller: Intel Corporation 82440MX AC'97 Audio Controller
00:00.2 Modem: Intel Corporation 82440MX AC'97 Modem Controller
00:02.0 VGA compatible controller: Silicon Motion, Inc. SM720 Lynx3DM (rev c1)
00:03.0 CardBus bridge: O2 Micro, Inc. OZ6933/711E1 CardBus/SmartCardBus Controller (rev 02)
00:03.1 CardBus bridge: O2 Micro, Inc. OZ6933/711E1 CardBus/SmartCardBus Controller (rev 02)
00:05.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
00:06.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 01)
00:07.0 ISA bridge: Intel Corporation 82440MX ISA Bridge (rev 01)
00:07.1 IDE interface: Intel Corporation 82440MX EIDE Controller
00:07.2 USB Controller: Intel Corporation 82440MX USB Universal Host Controller
00:07.3 Bridge: Intel Corporation 82440MX Power Management Controller
ssolari@ssolari-TravelMate-C100:~$ lsusb
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
ssolari@ssolari-TravelMate-C100:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:02:2d:b3:7a:08  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:10 Base address:0x100

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:96 errors:0 dropped:0 overruns:0 frame:0
          TX packets:96 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:7584 (7.5 KB)  TX bytes:7584 (7.5 KB)

ssolari@ssolari-TravelMate-C100:~$ iwconfig
lo        no wireless extensions.

irda0     no wireless extensions.

eth0      IEEE 802.11b  ESSID:"BRD83"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: None   
          Bit Rate:11 Mb/s   Sensitivity:1/0  
          Retry limit:8   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-122 dBm  Noise level=-122 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:6
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ssolari@ssolari-TravelMate-C100:~$ lsmod | grep "orinoco"
orinoco_cs             12898  1
orinoco                70112  1 orinoco_cs
cfg80211              172392  1 orinoco
pcmcia                 39822  1 orinoco_cs
pcmcia_core            21511  4 orinoco_cs,pcmcia,yenta_socket,pcmcia_rsrc
ssolari@ssolari-TravelMate-C100:~$ dmesg | grep "orinoco"
[   33.815740] orinoco 0.15 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[   33.996230] orinoco_cs 2.0: Hardware identity 0005:0004:0005:0000
[   33.996352] orinoco_cs 2.0: Station identity  001f:0001:0008:000a
[   33.996362] orinoco_cs 2.0: Firmware determined as Lucent/Agere 8.10
[   34.270134] orinoco_cs 2.0: Hardware identity 0005:0004:0005:0000
[   34.270266] orinoco_cs 2.0: Station identity  001f:0002:0009:0030
[   34.270277] orinoco_cs 2.0: Firmware determined as Lucent/Agere 9.48
[   34.270285] orinoco_cs 2.0: Ad-hoc demo mode supported
[   34.270292] orinoco_cs 2.0: IEEE standard IBSS ad-hoc mode supported
[   34.270299] orinoco_cs 2.0: WEP supported, 104-bit key
[   34.270306] orinoco_cs 2.0: WPA-PSK supported
ssolari@ssolari-TravelMate-C100:~$ sudo lshw -C network
[sudo] password for ssolari:
  *-network               
       description: Wireless interface
       physical id: 2
       logical name: eth0
       serial: 00:02:2d:b3:7a:08
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=orinoco_cs driverversion=3.0.0-12-generic firmware=Lucent/Agere 9.48 link=no multicast=yes wireless=IEEE 802.11b
ssolari@ssolari-TravelMate-C100:~$ iwlist scan
lo        Interface doesn't support scanning.

irda0     Interface doesn't support scanning.

eth0      No scan results

ssolari@ssolari-TravelMate-C100:~$ lsb_release -d
Description:	Ubuntu 11.10
ssolari@ssolari-TravelMate-C100:~$ uname -mr
3.0.0-12-generic i686
ssolari@ssolari-TravelMate-C100:~$ sudo /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                   [ OK ]
ssolari@ssolari-TravelMate-C100:~$

---

### Post by mambazo9 on 2012-01-14
I have exactly the same Wireless card, and exactly the same issue. Did this get solved yet?

---

