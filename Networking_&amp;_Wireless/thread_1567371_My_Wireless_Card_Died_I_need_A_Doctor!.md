---
title: "My Wireless Card Died I need A Doctor!"
date: 2010-09-03
forum: Networking &amp; Wireless
---

### Post by ChrisEiffel on 2010-09-03
Hi
 
My wireless card
product: Wireless WiFi Link 5300
vendor: Intel Corporation
Died recently. It was working wonderfully. It later started disconnecting from networks and not it is not operable. I need a wireless card doctor to tell me what is wrong with it and how I can fix it.
 
When I right click on the wireless icon in the top panel in ubuntu I get 
 
check Enable Networking
NO CHECK Enable Wireless (I cannot turn on)
check enable notifications
 
My ethernet is working
 
I tried
 
sudo ifconfig wlan0 up 
 
I get the error 
 
SIOCSIFFLAGS: Unknown Error 132
 
Here are some outputs
 
@ sudo lshw -C network
 
*-network DISABLED
description: Wireless interface
product: Wireless WiFi Link 5300
vendor: Intel Corporation
physical id: 0
bus info: pci@0000:06:00.0
logical name: wlan0
version: 00
serial: 00:21:6a:74:0b:92
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abgn
resources: irq:37 memory:db100000-db101fff
*-network
description: Ethernet interface
product: NetLink BCM57780 Gigabit Ethernet PCIe
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:07:00.0
logical name: eth0
version: 01
serial: 00:26:22:de:ac:3c
size: 10MB/s
capacity: 1GB/s
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.102 duplex=half firmware=sb latency=0 link=no multicast=yes port=MII speed=10MB/s
resources: irq:36 memory:da100000-da10ffff
*-network DISABLED
description: Ethernet interface
physical id: 3
logical name: vboxnet0
serial: 0a:00:27:00:00:00
capabilities: ethernet physical
configuration: broadcast=yes multicast=yes
 
@ sudo iwconfig
 
wlan0 IEEE 802.11abgn ESSID:off/any 
Mode:Managed Access Point: Not-Associated Tx-Power=off 
Retry long limit:7 RTS thr:off Fragment thr:off
Encryption key:off
Power Management:off
 
@ sudo ifconfig
eth0 Link encap:Ethernet HWaddr 00:26:22:de:ac:3c 
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt:18 
lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:164 errors:0 dropped:0 overruns:0 frame:0
TX packets:164 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:9924 (9.9 KB) TX bytes:9924 (9.9 KB)
 
@ sudo nm-tool
 
NetworkManager Tool
State: disconnected
- Device: eth0 -----------------------------------------------------------------
Type: Wired
Driver: tg3
State: unavailable
Default: no
HW Address: 00:26:22:DE:AC:3C
Capabilities:
Carrier Detect: yes
Speed: 10 Mb/s
Wired Properties
Carrier: off
 
- Device: wlan0 ----------------------------------------------------------------
Type: 802.11 WiFi
Driver: iwlagn
State: unavailable
Default: no
HW Address: 00:21:6A:74:0B:92
Capabilities:
Wireless Properties
WEP Encryption: yes
WPA Encryption: yes
WPA2 Encryption: yes
Wireless Access Points 
 
 @ sudo dmesg | grep iwlagn
 
[ 20.777373] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
[ 20.777377] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[ 20.777469] iwlagn 0000:06:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 20.777479] iwlagn 0000:06:00.0: setting latency timer to 64
[ 20.777526] iwlagn 0000:06:00.0: Detected Intel Wireless WiFi Link 5300AGN REV=0x24
[ 20.812587] iwlagn 0000:06:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels

---

### Post by Tracy177 on 2010-09-03
it look like your card is ok 

and i would suggest you to boot up windows download WICD remove network manager install wicd and than try it again.

i had the same problem with network manager ones it worked other time was showing networking off and i couldnt switch it on so i installed wicd and didnt have even one problem since

---

### Post by ChrisEiffel on 2010-09-03
Hi
 
I was searching around on the **SIOCSIFFLAGS: Unknown error 132**  
 
I found some vague references to rfkill.
 
@ rfkill list
0: phy0: Wireless LAN
     Soft Blocked: no
     Hard Blocked:yes
 
It says my "hardware is blocked"

---

### Post by Tracy177 on 2010-09-03
> **ChrisEiffel said:**
> Hi
 
I was searching around on the **SIOCSIFFLAGS: Unknown error 132**  
 
I found some vague references to rfkill.
 
@ rfkill list
0: phy0: Wireless LAN
     Soft Blocked: no
     Hard Blocked:yes
 
It says my "hardware is blocked"


i think u pressed the off network button press it again and it will work u have got laptop so there is button to switch network on and off

---

### Post by Iowan on 2010-09-03
I presume you've right-clicked the Network Manager icon and verified Networking and Wireless are enabled. 
A few links that *might* be helpful:
[http://ubuntuforums.org/showthread.php?t=1564615]("http://ubuntuforums.org/showthread.php?t=1564615")
[http://ubuntuforums.org/showthread.php?t=1505217]("http://ubuntuforums.org/showthread.php?t=1505217")

As I recall, */var/lib/NetworkManager/NetworkManager.state* has a line about wireless... though I'm not sure these would qualify as "Hard Blocked" - that seems more like a switch...

---

### Post by ChrisEiffel on 2010-09-03
I apoligize 
 
This had nothing to do with ubuntu and everything to do with bad computer design
 
There is this little switch on the side of my computer that is not labled, that when I fliped it, my wireless card worked. 
 
Thank you for your help. Sometimes it is that easy.

---

