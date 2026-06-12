---
title: "belkin wireless troubles PCI F5D7000-W"
date: 2008-12-10
forum: Networking &amp; Wireless
---

### Post by Dave Vader on 2008-12-10
Hello, I have been trying fruitlessly for the last month to get my PC online with Ubuntu. My thomson 121g wouldn't work no matter what I tried, so I bought a D-link G-122 which wouldn't work either. I have since found a belkin PCI card in the back of my PC which with an ariel extension gets the best reception of the 3 in windows at 54mbps. However, ubuntu 8.10 still can't get it to run.
I have used ndiswrapper with the native windows driver, but when i try to use it it will not configure still. I have gone back to using the native drivers (b43, b43legacy and ssb) in ubuntu, and still no joy. It says the access point is disassociated, and the network is disabled. I think this might be the root of it, but I am an absolute novice at this. I really don't want to have to use windows anymore as it's driving me nuts. My PC is in the garage, and so has no wired access point, so any suggestions will have to involve dual booting and memory drives. Thanks in advance, and here are a whole load of readouts as suggested in the sticky thread at the top.

belkin f5d7000-w PCI 54g wireless card

 lspci
00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 12)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 12)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 12)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 12)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 12)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 12)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio Controller (rev 12)
00:1f.6 Modem: Intel Corporation 82801BA/BAM AC'97 Modem Controller (rev 12)
01:00.0 VGA compatible controller: nVidia Corporation NV11DDR [GeForce2 MX200] (rev b2)
02:01.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)
02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)


 lsusb
Bus 002 Device 002: ID 07ab:fccb Freecom Technologies 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 046d:c00b Logitech, Inc. MouseMan Wheel
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:40:ca:b5:a9:5e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:240 errors:0 dropped:0 overruns:0 frame:0
          TX packets:240 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15040 (15.0 KB)  TX bytes:15040 (15.0 KB)

 iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.



 wlan0
wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


 lsmod
Usage: lsmod



dmesg
[    0.590283] PCI: 0000:02:01.0 reg 10 32bit mmio: [ef000000, ef001fff]
[    3.987475] b43-pci-bridge 0000:02:01.0: PCI INT A -> Link[LNK0] -> GSI 9 (level, low) -> IRQ 9
[    3.991696] ssb: Sonics Silicon Backplane found on PCI device 0000:02:01.0


sudo lshw -C network
[sudo] password for dave: 
  *-network:0             
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32 module=ssb
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: eth0
       version: 10
       serial: 00:40:ca:b5:a9:5e
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=32 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:30:bd:f2:17:b6
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 0a:0d:13:5c:98:c5
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

pan0      Interface doesn't support scanning.

iwlist scan wlan0
iwlist: unknown command `wlan0' (check 'iwlist --help').

ubuntu release 8.10
kernel 2.6.27-7-generic i686

sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                   [ OK ]

---

### Post by albinootje on 2008-12-10
Just a wild guess, but from experience with some other card in the past.
With certain wifi-cards you need to give it an address first, before it actually will become "alive".
I once came across a wifi-card (some SMC pci-card) which seemed to be available to work with, but dhclient and iwlist scan didn't do anything.
Until a friend of mine was passing by, and he gave it some random ip-address, and then dhclient and iwlist scan did work.
Why not give it a try, it can't hurt.

---

### Post by Dave Vader on 2008-12-10
> **albinootje said:**
> Just a wild guess, but from experience with some other card in the past.
With certain wifi-cards you need to give it an address first, before it actually will become "alive".
I once came across a wifi-card (some SMC pci-card) which seemed to be available to work with, but dhclient and iwlist scan didn't do anything.
Until a friend of mine was passing by, and he gave it some random ip-address, and then dhclient and iwlist scan did work.
Why not give it a try, it can't hurt.
Sounds like a plan, however, as a total newbie to linux, I wouldn't know where to start. Could you please elaborate a little for me please? Sorry to be a pain, but treat me as if I know absolutely nothing about anything.

---

### Post by Dave Vader on 2008-12-11
bump

---

### Post by Dave Vader on 2008-12-13
double bump

---

### Post by Kevbert on 2008-12-13
If you go to /lib/firmware you should have two directories b43 and b43legacy which are the drivers for your card. Have you seen this [[COLOR="Red"]post[/COLOR]]("http://ubuntuforums.org/showthread.php?t=766560") which is one of the best for your card ?  If you need the two (firmware) directories they are [COLOR="Red"][here]("http://ubuntuforums.org/showpost.php?p=5469730&postcount=13")[/COLOR].
Either method should work, once you've got rid of the current ndiswrapper drivers.

---

### Post by Dave Vader on 2008-12-14
Brilliant, the firmware wasn't there, have downloaded it and chucked it in the folder and it seems to be working now. Thank you so very much

---

