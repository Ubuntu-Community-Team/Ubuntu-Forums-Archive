---
title: "Can't connect to WiFi via command line (iwconfig/ifconfig)"
date: 2011-07-03
forum: Networking &amp; Wireless
---

### Post by veraction on 2011-07-03
Hi,

I'm unable to connect to my unsecured wireless network (or any wireless network) on my laptop, though Network Manager connects fine. (Also, my phone and other computers have no problem connecting.) I've googled this extensively and have found no answers. 


Computer: Toshiba NB505 netbook, running a fresh install of Ubuntu 11.04
```

$ lspci | grep Network
07:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)

```

Initial settings on startup (before logging into Gnome and having Network Manager start)
```

$ ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 7c:4f:b5:73:b4:be  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
$ iwconfig wlan0
wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off          

```

Attempting to configure wireless on command line:

```

$ sudo iwlist wlan0 scan
wlan0     Scan completed :
*Edited to only show the relevant network*
          Cell 04 - Address: 00:16:01:12:E7:5E
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=64/70  Signal level=-46 dBm  
                    Encryption key:off
                    ESSID:"foobarweb"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000000b6d6419d
                    Extra: Last beacon: 224ms ago
                    IE: Unknown: 0009666F6F626172776562
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0102
                    IE: Unknown: 2F0102
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180201F0000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
$ # At this point, it would seem to me that I just need to configure wlan0 to use the appropriate essid, since it already is in Managed mode and there is no encryption
$ sudo iwconfig wlan0 essid "foobarweb"
$ sudo iwconfig wlan0 # double check that the essid was set
wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Encryption key:off
          Power Management:off
$ # Not sure why that wasn't set. Try setting more things:
$ sudo iwconfig wlan0 key open mode Managed essid "foobarweb" channel 6
$ sudo iwconfig wlan0 # check to see if settings took hold this time
wlan0     IEEE 802.11bgn  ESSID:"foobarweb"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Encryption key:off
          Power Management:off
$ # ok, everything's set, let's try to get an IP address
$ sudo dhclient -v wlan0  
Internet Systems Consortium DHCP Client 4.1.1-P1
Copyright 2004-2010 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/wlan0/7c:4f:b5:73:b4:be
Sending on   LPF/wlan0/7c:4f:b5:73:b4:be
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

This is where I'm stuck. I've checked the syslog when Network Manager connects and it seems to get a DHCPOFFER and ip address immediately every time.

By the way, here's the iwconfig/ifconfig settings that are set when Network Manager is used:
```

$ sudo ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 7c:4f:b5:73:b4:be  
          inet addr:192.168.1.119  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::7e4f:b5ff:fe73:b4be/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:37 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1404 (1.4 KB)  TX bytes:9312 (9.3 KB)
$ sudo iwconfig wlan0
wlan0     IEEE 802.11bgn  ESSID:"foobarweb"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:16:01:12:E7:5E   
          Bit Rate=5.5 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=70/70  Signal level=-37 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

[edit]
I've now started up wireshark on both this laptop and another one, monitoring for DHCP packets. With Network Manager initializing the wireless configuration, I see the normal sequence of DHCP packets on both systems. With the manual approach above, I see no packets whatsoever. Even when "dhclient" shows that it is sending DHCPDISCOVER packets, I see nothing in wireshark.

---

### Post by chili555 on 2011-07-03
Manual methods iwconfig, etc. are unlikely to work as long as Network Manager is running. NM has taken control and will not respond to another set of hands on the controls. You might be able to remove NM from the startup programs and get it done, but why if NM connects as expected. Check with:```
ps aux | grep -i network
```If you are simply old-school and want to do things your way, then I'd suggest removing NM altogether.

In my various and growing collection of systems, both NM and manual methods, where NM is removed, work perfectly.

---

### Post by veraction on 2011-07-03
Thanks!

That was the solution. I had assumed that Network Manager was not running since I had not logged in on an X console and had assumed Network Manager was only run when Gnome/etc was started since it is applet based. I even did ran grep through ps but for the wrong name ("nm" or "network").

Needless to say, I did find that a process called NetworkManager was running. Stopping it via the following command made everything work:

```

$ sudo service network-manager stop

```

From then, all I needed to do was:
```

$ sudo iwconfig wlan0 essid $SSID # it sets the essid properly now, without needing to set the key to open, etc.
$ sudo dhclient -v wlan0
$ # now I have an IP

```

As to the reason for doing things manually like this, it is primarily for learning purposes, but also because there are times when I don't want to run X at all (and if I do, I just use fluxbox or some other lightweight window manager)

---

