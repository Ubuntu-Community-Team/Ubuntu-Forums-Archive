---
title: "Dell B130 - Almost working"
date: 2006-06-11
forum: Networking &amp; Wireless
---

### Post by Jerim on 2006-06-11
I am so close I can almost taste it. It looks like the wirless card is working. The card is working and can obviously see the local networks. This is what I get when I do  "iwlist eth1 scan"

[I]eth1      Scan completed :
          Cell 01 - Address: 00:14:BF:F6:70:3F
                    ESSID:"XXXXX"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Quality=100/100  Signal level=-167 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 328ms ago
          Cell 02 - Address: 00:0C:10:21:32:01
                    ESSID:"XXXX"
                    Protocol:IEEE 802.11b
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:11 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 11
                    Quality=100/100  Signal level=-177 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 172ms ago
[/I]
Ubuntu will tell me that I am connected to the network, and will let me set wirless to the gateway, but I don't get any signal strenght even with the laptop sitting right next to the router, and I can't geat an IP address. (Static IP's don't work either.) Cell 02 is what I am trying to connect with.(Keep in mind I purposefly changed the network names to all X's for obvious reasons.) Wifi-radar won't find any networks automatically, I have to manually create one. After I connect to the network using wifi-radar, here is what I get:

[I]Stale pid file.  Removing
Unsupported driver '-P'.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth1/00:14:a4:58:bd:bc
Sending on   LPF/eth1/00:14:a4:58:bd:bc
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 18[/I]

I tried blaclisting my network card which was suggested elsewhere and that seem to momentarily help the situation as some networks were automatically detected. But it didn't fix the problem, so I un-blacklisted it. I am seeing so many different ways to connect, I don't know which way is up. 

Inorder to use wifi-radar do I HAVE to blacklist the device? (I noticed that when I blacklisted it, it didn't show up in network manager. It still seemed to work though.)

Any help would be appriciated. Even a point toward a working solution would be appreciated. Please understand that I have done most of the basics, such as ndiswrapper.

---

### Post by Jerim on 2006-06-11
Okay, I just found something odd. My wireless network is listed as eth1 in the network settings panel. However, if I do "dmesg | grep  ndis" I get this:

[[I]4294705.316000] ndiswrapper version 1.8 loaded (preempt=yes,smp=no)
[4294705.429000] ndiswrapper: driver bcmwl5 (Broadcom,11/02/2005, 4.10.40.0) loaded
[4294705.437000] ndiswrapper: using irq 209
[4294706.447000] wlan0: ndiswrapper ethernet device 00:14:a4:58:bd:bc using driver bcmwl5, 14E4:4318.5.conf[/I]

So somewhere, it seems to also be loading my wireless card as wlan0. If I do iwconfig, I get;

[I]lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:off/any  Nickname:"XXXX"
          Mode:Auto  Frequency:2.462 GHz  Access Point: Not-Associated
          Bit Rate=54 Mb/s   Tx-Power:25 dBm
          RTS thr=2347 B   Fragment thr=2346 B
          Power Management min timeout:0us  mode:All packets received
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0[/I]

There is no mention  of wlan0. If I do ifconfig, I get;

[I]eth0      Link encap:Ethernet  HWaddr 00:14:22:92:B0:00
          inet addr:192.168.100.5  Bcast:192.168.100.255  Mask:255.255.255.0
          inet6 addr: fe80::214:22ff:fe92:b000/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5920 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11784 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:4439025 (4.2 MiB)  TX bytes:1185164 (1.1 MiB)
          Interrupt:217

eth1      Link encap:Ethernet  HWaddr 00:14:A4:58:BD:BC
          inet6 addr: fe80::214:a4ff:fe58:bdbc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
[/I]

Again, no mention of wlan0. I have used ndiswrapper at one point to load the driver for the card. I am not sure if ndiswrapper is needed, if the card is loaded in "networking settings." When I do "iwlist eth1 scan" I get:
[I]
eth1      No scan results[/I]

If I do "iwlist wlan0 scan" I get:

*wlan0     Interface doesn't support scanning.*

This is the first time I am seeing wlan0 listed anywhere, in over a week of working through tutorials. I am not sure what to do here. I do have bcm4xx blacklisted but eth1 still shows up in "network settings." My problem may be because eth1 and wlan0 are the same thing and Ubuntu is getting confused.

---

### Post by thedevnull on 2006-06-19
Hello,

  This is the exact problem I am seeing.  Did you find any resolution to it?

Thanks in advance

---

