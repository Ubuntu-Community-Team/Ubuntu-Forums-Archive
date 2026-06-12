---
title: "Wireless Connection but no internet access"
date: 2010-12-06
forum: Networking &amp; Wireless
---

### Post by Jim_Hope on 2010-12-06
I had been happily using a wireless connection for about two weeks. The connection then went down for a few days. Since it came back up, I can connect to the network, but cannot access the internet. Other users of the network can both connect to the network, and access the internet, though people have experienced the same problem as me the last time the network went down (they could connect to the network but not access the internet).
   
  I have tried deleting and re-starting the connection, to no avail. I have looked around the forums, but haven't found anything that can help: do any of you have any suggestions? I am malarial and at the end of tether.
   
  It is not a problem with Ipv6, which is set to ignore, as it was in the past when the connection worked.
   
  I am running Ubuntu 10.10 on an X61 Thinkpad. Below is the output of iwconfig, route -n, lspci, and what happens when I ping other network addresses/www.google.com.
   
  Any help gratefully appreciated,
   
  cheers,
   
  Jim
   
  Iwconfig:
   
  eth0 Link encap:Ethernet HWaddr 00:1d:72:9e:09:8f 
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt:20 Memory:fe000000-fe020000 

lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:6524 errors:0 dropped:0 overruns:0 frame:0
TX packets:6524 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:220847 (220.8 KB) TX bytes:220847 (220.8 KB)

wlan0 Link encap:Ethernet HWaddr 00:1b:77:41:7d:d4 
inet addr:192.168.107.52 Bcast:192.168.107.255 Mask:255.255.255.0
inet6 addr: fe80::21b:77ff:fe41:7dd4/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:2887 errors:0 dropped:0 overruns:0 frame:0
TX packets:4831 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:436227 (436.2 KB) TX bytes:386110 (386.1 KB)

lo no wireless extensions.

eth0 no wireless extensions.

wlan0 IEEE 802.11abg ESSID:"The British Institute" 
Mode:Managed Frequency:2.462 GHz Access Point: 00:11:6B:E0:4E:A4 
Bit Rate=54 Mb/s Tx-Power=15 dBm 
Retry long limit:7 RTS thr:off Fragment thr:off
Encryption key:off
Power Management:off
Link Quality=62/70 Signal level=-48 dBm 
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

vboxnet0 no wireless extensions.
   
  Kernel IP routing table
   
  Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
   
  192.168.107.0   0.0.0.0         255.255.255.0   U     2      0        0 wlan0
   
  169.254.0.0     0.0.0.0         255.255.0.0         U     1000   0        0 wlan0
   
  0.0.0.0         192.168.107.21  0.0.0.0             UG    0      0        0 wlan0
   
   
  LSPCI:
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:19.0 Ethernet controller: Intel Corporation 82566MM Gigabit Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HBM (ICH8M-E) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
05:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
05:00.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04)
05:00.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 21)
   
  PING 192.168.1.254 (192.168.1.254) 56(84) bytes of data.
   
  --- 192.168.1.254 ping statistics ---
   
  7 packets transmitted, 0 received, 100% packet loss, time 5999ms
   
   
  PING [www.google.com](www.google.com) (72.14.204.104) 56(84) bytes of data.
   
   
   
  --- [www.google.com](www.google.com) ping statistics ---
   
  13 packets transmitted, 0 received, 100% packet loss, time 12094ms
   
   
  
 
 
  [FONT=&quot] [/FONT]

---

### Post by dineshs on 2010-12-06
What about ```
ping -c3 4.2.2.1
```and what is 192.168.1.254?

---

### Post by Jim_Hope on 2010-12-06
Thanks for getting back to me so quickly dineshs. It turned out the network was not recognizing my IP. I manually entered an IP address, got only skype working, then entered the DNS servers, and everything worked.

---

