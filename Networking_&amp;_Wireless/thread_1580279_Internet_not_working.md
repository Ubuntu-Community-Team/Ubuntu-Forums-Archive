---
title: "Internet not working"
date: 2010-09-23
forum: Networking &amp; Wireless
---

### Post by Rokugatsu on 2010-09-23
Hi!

First of all, sorry for my english, its not my first language :P

The problem is that I installed Ubuntu but my wireless internet is not working. It seems like ubuntu can see my wifi thing (the thing i put to my usb port to get the internet :P) but it can't see any networks. 
I tried to add my network manualy. I did it and it seems like there is internet but its not coz browser and anything that need connection to the internet is not working.

On other forums they asked me to give them this:
lsusb
lspci
lshq-c
inconfig
iwconfig

So maybe you will need it:

> roku@roku-desktop:~/Pulpit$ isisb 
isisb: command not found 
roku@roku-desktop:~/Pulpit$ 
roku@roku-desktop:~/Pulpit$ lsusb 
Bus 002 Device 004: ID 04ca:002f Lite-On Technology Corp. 
Bus 002 Device 003: ID 0df6:003f Sitecom Europe B.V. 
Bus 002 Device 002: ID 8087:0020 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 001 Device 004: ID 0bda:0151 Realtek Semiconductor Corp. Mass Stroage Device 
Bus 001 Device 003: ID 046d:c054 Logitech, Inc. 
Bus 001 Device 002: ID 8087:0020 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
roku@roku-desktop:~/Pulpit$ ispci 
No command 'ispci' found, did you mean: 
Command 'lspci' from package 'pciutils' (main) 
ispci: command not found 
roku@roku-desktop:~/Pulpit$ lspci 
00:00.0 Host bridge: Intel Corporation Clarkdake DRAM Controller (rev 12) 
00:01.0 PCI bridge: Intel Corporation Clarkdale PCI Express x16 Root Port (rev 12) 
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06) 
00:19.0 Ethernet controller: Intel Corporation 82578DC Gigabit Network Connection (rev 06) 
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06) 
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06) 
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06) 
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06) 
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 06) 
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 06) 
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 06) 
00:1c.6 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 7 (rev 06) 
00:1c.7 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 8 (rev 06) 
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06) 
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a6) 
00:1f.0 ISA bridge: Intel Corporation 5 Series Chipset LPC Interface Controller (rev 06) 
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 06) 
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06) 
01:00.0 VGA compatible controller: nVidia Corporation Device 0ca2 (rev a2) 
01:00.1 Audio device: nVidia Corporation Device 0be4 (rev a1) 
06:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. Device 3403 
roku@roku-desktop:~/Pulpit$ lshw-c network 
lshw-c: command not found 
roku@roku-desktop:~/Pulpit$ lshw -C 
Hardware Lister (lshw) - B.02.14 
usage: lshw [-format] [-options ...] 
lshw -version 

-version print program version (B.02.14) 

format can be 
-html output hardware tree as HTML 
-xml output hardware tree as XML 
-short output hardware paths 
-businfo output bus information 

options can be 
-class CLASS only show a certain class of hardware 
-C CLASS same as '-class CLASS' 
-c CLASS same as '-class CLASS' 
-disable TEST disable a test (like pci, isapnp, cpuid, etc. ) 
-enable TEST enable a test (like pci, isapnp, cpuid, etc. ) 
-quiet don't display status 
-sanitize sanitize output (remove sensitive information like serial numbers, etc.) 
-numeric output numeric IDs (for PCI, USB, etc.) 

roku@roku-desktop:~/Pulpit$ ifconfig 
eth0 Link encap:Ethernet HWaddr 90:fb:a6:48:40:d9 
UP BROADCAST MULTICAST MTU:1500 Metric:1 
RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B) 
Memory:f9fc0000-f9fe0000 

lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0 
inet6 addr: ::1/128 Scope:Host 
UP LOOPBACK RUNNING MTU:16436 Metric:1 
RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
collisions:0 txqueuelen:0 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B) 

wlan0 Link encap:Ethernet HWaddr 00:0c:f6:53:3a:26 
inet addr:10.42.43.1 Bcast:10.42.43.255 Mask:255.255.255.0 
inet6 addr: fe80::20c:f6ff:fe53:3a26/64 Scope:Link 
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1 
RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
TX packets:25 errors:0 dropped:0 overruns:0 carrier:0 
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 B) TX bytes:4391 (4.3 KB) 

wmaster0 Link encap:UNSPEC HWaddr 00-0C-F6-53-3A-26-00-00-00-00-00-00-00-00-00-00 
UP RUNNING MTU:0 Metric:1 
RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B) 

roku@roku-desktop:~/Pulpit$ iwconfig 
lo no wireless extensions. 

eth0 no wireless extensions. 

wmaster0 no wireless extensions. 

wlan0 IEEE 802.11bgn ESSID:"34178560" 
Mode:Ad-Hoc Frequency:2.412 GHz Cell: 2E:F5:BC:75:B6:6C 
Tx-Power=18 dBm 
Retry long limit:7 RTS thrff Fragment thrff 
Power Managementff 
Link Quality:0 Signal level:0 Noise level:0 
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0 
Tx excessive retries:0 Invalid misc:0 Missed beacon:0 

roku@roku-desktop:~/Pulpit$

Hope you understoond what I wrote and you can help me :D

---

### Post by grahammechanical on 2010-09-23
I am not someone who understands the output of those terminal commands. So, I ask - what information do you see if you right and left click on the network manager icon? Is your modem swtiched on? Network manager will not see any wireless networks if there are none operating within range. This is why I ask if the modem is switched on. What do the indicator lights on the modem reveal? Is the wifi thing plugged into a USB port before you start Ubuntu? Was it plugged in when you installed Ubuntu? During the installation the hardware in the computer is probed and the correct modules installed. If the installer did not know that you were using a USB wireless device (correct name) then it would not install the drivers for that device. I am just trying to think of simple things that might help you. That is the level that I am at.

By the way, the world's universal language is not English but Broken English. I speak English and Rubbish. :)

regards

---

### Post by Rokugatsu on 2010-09-23
With my modem and internet everything's ok, because Im useing it now ;) 
Im on windows 7 now (I have 2 systems on this moment on my PC till I menage how to make internet on Ubuntu) and everything works. I also had Linux on my previous PC and internet worked just after I installed Linux, there was no problem with it like its now.

When I click on menager it says "wirless network connections" (dont know exacly what it says coz I have polish menu in Linux, this is just my translation :P) but there is no connections and it should be like 2 or 3 (one of them is mine and 2 others from houses next to me).

USB thingy was plugged to my PC when I was installing Linux, yes :)

> By the way, the world's universal language is not English but Broken English.
Hehe, I can speak Broken English perfectly then :D

---

### Post by Iowan on 2010-09-23
*Looks* like the wireless card has an IP address. 

Another useful command is **sudo lshw -C network**

---

### Post by Rokugatsu on 2010-09-24
Hope you are not going to kill me but I installed other Ubuntu. Ubuntu 10.4. Was hoping it might work on other version but nah, same problem.

So, all commands once again (including lshw -C network)

> roku@roku-desktop:~$ lsusb 
Bus 002 Device 005: ID 04ca:002f Lite-On Technology Corp. 
Bus 002 Device 004: ID 1977:0824 T-Logic 
Bus 002 Device 003: ID 0df6:003f Sitecom Europe B.V. 
Bus 002 Device 002: ID 8087:0020   
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 001 Device 004: ID 0bda:0151 Realtek Semiconductor Corp. Mass Storage Device 
Bus 001 Device 003: ID 046d:c054 Logitech, Inc. 
Bus 001 Device 002: ID 8087:0020   
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
roku@roku-desktop:~$ lspci 
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 12) 
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 12) 
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06) 
00:19.0 Ethernet controller: Intel Corporation 82578DC Gigabit Network Connection (rev 06) 
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06) 
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06) 
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06) 
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06) 
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 06) 
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 06) 
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 06) 
00:1c.6 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 7 (rev 06) 
00:1c.7 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 8 (rev 06) 
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06) 
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a6) 
00:1f.0 ISA bridge: Intel Corporation 5 Series Chipset LPC Interface Controller (rev 06) 
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 06) 
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06) 
01:00.0 VGA compatible controller: nVidia Corporation Device 0ca2 (rev a2) 
01:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1) 
06:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. Device 3403 
roku@roku-desktop:~$ sudo lshw -C network 
[sudo] password for roku: 
  *-network                
       description: Ethernet interface 
       product: 82578DC Gigabit Network Connection 
       vendor: Intel Corporation 
       physical id: 19 
       bus info: pci@0000:00:19.0 
       logical name: eth0 
       version: 06 
       serial: 90:fb:a6:48:40:d9 
       capacity: 1GB/s 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.0.2-k2 firmware=0.12-5 latency=0 link=no multicast=yes port=twisted pair 
       resources: irq:37 memory:f9fc0000-f9fdffff memory:f9ffc000-f9ffcfff ioport:cc00(size=32) 
  *-network 
       description: Wireless interface 
       physical id: 2 
       logical name: wlan0 
       serial: 00:0c:f6:53:3a:26 
       capabilities: ethernet physical wireless 
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bgn 

roku@roku-desktop:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 90:fb:a6:48:40:d9   
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Memory:f9fc0000-f9fe0000 

lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:88 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:88 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:6784 (6.7 KB)  TX bytes:6784 (6.7 KB) 

wlan0     Link encap:Ethernet  HWaddr 00:0c:f6:53:3a:26   
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 

roku@roku-desktop:~$ iwconfig 
lo        no wireless extensions. 

eth0      no wireless extensions. 

wlan0     IEEE 802.11bgn  ESSID:off/any   
          Mode:Managed  Access Point: Not-Associated   Tx-Power=18 dBm    
          Retry  long limit:7   RTS thr:off   Fragment thr:off 
          Power Management:on 

---

### Post by Rokugatsu on 2010-09-25
Anyone? [-o<

---

