---
title: "wireless: can't associate with access point in kde, wireless in gnome works fine"
date: 2010-04-30
forum: Networking &amp; Wireless
---

### Post by typiCAL_ on 2010-04-30
First, I'm sorry to open another one of these "WiFi works in Gnome, not in KDE" threads, but I have been all over google and hundreds of threads across different sites and can't figure this one out.

As mentioned, wireless is peachy in Gnome, unfortunately I like KDE and I'm more productive using it (when I have internet).  Wired network works fine in KDE, and my network card
```
03:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
        Subsystem: Intel Corporation Device 1201
        Flags: bus master, fast devsel, latency 0, IRQ 31
        Memory at d6200000 (64-bit, non-prefetchable) [size=8K]
        Capabilities: <access denied>
        Kernel driver in use: iwlagn
        Kernel modules: iwlagn

```shows just fine.  I can scan for networks, see them, and attempt to connect, but it just doesn't seem to associate with the access point after authenticating (meaning you don't need to scold me about making sure my WPA/WEP key is correct):
```
$ dmesg | tail
[ 2591.005761] r8169: eth0: link down
[ 2693.094361] wlan0: direct probe to AP 00:13:10:da:c1:26 (try 1)
[ 2693.096958] wlan0: direct probe responded
[ 2693.096965] wlan0: authenticate with AP 00:13:10:da:c1:26 (try 1)
[ 2693.099682] wlan0: authenticated
[ 2693.099716] wlan0: associate with AP 00:13:10:da:c1:26 (try 1)
[ 2693.290150] wlan0: associate with AP 00:13:10:da:c1:26 (try 2)
[ 2693.490074] wlan0: associate with AP 00:13:10:da:c1:26 (try 3)
[ 2693.690138] wlan0: association with AP 00:13:10:da:c1:26 timed out
[ 2766.822918] wlan0: direct probe to AP 00:13:10:da:c1:26 (try 1)
[ 2767.020138] wlan0: direct probe to AP 00:13:10:da:c1:26 (try 2)
[ 2767.220146] wlan0: direct probe to AP 00:13:10:da:c1:26 (try 3)
[ 2767.420157] wlan0: direct probe to AP 00:13:10:da:c1:26 timed out
[ 2827.490562] r8169: eth0: link up

```This happens when manually configuring wlan0 with ifconfig and iwconfig
```
$ ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:1e:65:13:68:0e  
          inet addr:192.168.3.117  Bcast:192.168.3.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
$ iwconfig wlan0 ap 00:13:10:DA:C1:26
$ iwconfig wlan0
wlan0     IEEE 802.11abgn  ESSID:"Control"  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
```and when trying to use DHCP:
```
$ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.1.3
<snip>
Listening on LPF/wlan0/00:1e:65:13:68:0e
Sending on   LPF/wlan0/00:1e:65:13:68:0e
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```As you see, I've tried doing it all manually, and YES I have tried using wicd and nm-applet instead of knetworkmanager, still no dice.  If you have *anything*, or need to know anything else about my system, feel free. :confused:

---

### Post by typiCAL_ on 2010-04-30
Okay, answered my own question, so sorry about the waste of thread space.  Turns out it was a mix between a problem with my router's leases, and my system running two network managers, both wicd and network-manager at the same time.  Made it kinda difficult to diagnose. =D

---

