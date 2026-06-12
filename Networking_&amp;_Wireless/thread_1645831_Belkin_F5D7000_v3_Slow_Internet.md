---
title: "Belkin F5D7000 v3 Slow Internet"
date: 2010-12-15
forum: Networking &amp; Wireless
---

### Post by shkm on 2010-12-15
Hello,

I'm experiencing very slow internet speeds with a Belkin Wireless-G Desktop Network Card (F5D7000uk) version 3000uk. To my knowledge this card has an rt2500 chipset, and Ubuntu is using the **rt2500pci** driver by default. Internet may be fine for a short while after rebooting, but after browsing a couple of pages it will slow to a crawl.

I've tried numerous fixes, however they were so numerous that I lost track of what I'd tried. As such, today I went with a complete re-install of 10.10. Internet seemed fine, but again slowed after a little use. Since re-installing, so far I've only tried

```
iwconfig wlan0 power off
```

to no avail.

Everything works fine on Windows, as does a notebook on the same network running 10.10.

I'm really eager to get this thing working, so any help would be greatly appreciated! I'd pick up a new card if only I could guarantee that it would work, but then others don't seem to be having this issue with this card. Also, before the re-install I tried using an Edimax USB wireless adapter, but to my knowledge it also exhibited slow internet.

**ifconfig**
```
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:11:50:8f:e2:68  
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:50ff:fe8f:e268/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:235091 errors:0 dropped:0 overruns:0 frame:0
          TX packets:128139 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:347759159 (347.7 MB)  TX bytes:13739223 (13.7 MB)
```

**iwconfig**
```
lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"Cthulhu"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:25:9C:CA:79:E0   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=64/70  Signal level=-46 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

**lspci**
```
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IB (ICH9) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IB (ICH9) 2 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G92 [GeForce 8800 GT] (rev a2)
03:00.0 IDE interface: JMicron Technology Corp. JMB368 IDE controller
05:02.0 Network controller: RaLink RT2500 802.11g (rev 01)

```

**ping**
```
PING www.l.google.com (74.125.77.99) 56(84) bytes of data.
64 bytes from ew-in-f99.1e100.net (74.125.77.99): icmp_req=1 ttl=54 time=2409 ms
64 bytes from ew-in-f99.1e100.net (74.125.77.99): icmp_req=2 ttl=54 time=2470 ms
64 bytes from ew-in-f99.1e100.net (74.125.77.99): icmp_req=3 ttl=54 time=2493 ms
64 bytes from ew-in-f99.1e100.net (74.125.77.99): icmp_req=4 ttl=54 time=19.4 ms
64 bytes from ew-in-f99.1e100.net (74.125.77.99): icmp_req=5 ttl=54 time=1241 ms
64 bytes from ew-in-f99.1e100.net (74.125.77.99): icmp_req=6 ttl=54 time=614 ms
64 bytes from ew-in-f99.1e100.net (74.125.77.99): icmp_req=7 ttl=54 time=16.0 ms
64 bytes from ew-in-f99.1e100.net (74.125.77.99): icmp_req=8 ttl=54 time=1880 ms
64 bytes from ew-in-f99.1e100.net (74.125.77.99): icmp_req=9 ttl=54 time=2388 ms
^C
--- www.l.google.com ping statistics ---
11 packets transmitted, 9 received, 18% packet loss, time 18453ms
rtt min/avg/max/mdev = 16.036/1503.741/2493.257/996.326 ms, pipe 3
```

**Full(ish) Specs**
Ubuntu 10.10
Intel Core 2 Quad Q6600
Gigabyte GA-P35-DS3L (v2, latest BIOS)
4GB Team Elite RAM
Geforce 8800 GT (with proprietary drivers)

Router is running DD-WRT and uses a WPA2 key
DNS server is OpenDNS
DHCP is enabled but router sets a local IP address based on MAC
Bit rate fluctuates -- on this boot it was showing 18Mb/s, now it's 54Mb/s and speed is slow

**Edit**
I disabled IPv6 and everything seemed OK for a while, until I tried a torrent. Ubuntu was downloading at a pathetic 90KB/s. Disconnected, inserted USB adapater and connected; download speed instantly shot up to 2.2MB/s. So there's definitely something up with the card.

---

