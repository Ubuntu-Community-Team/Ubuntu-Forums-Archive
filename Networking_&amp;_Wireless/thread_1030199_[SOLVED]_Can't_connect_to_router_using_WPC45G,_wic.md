---
title: "[SOLVED] Can't connect to router using WPC45G, wicd, WPA, StaticIP, Intrepid"
date: 2009-01-04
forum: Networking &amp; Wireless
---

### Post by rijidij on 2009-01-04
Please help. I have been trying to resolve this for days and am at my wits' end.

I have a very old laptop which is serving out its remaining days as my girlfriend's web browser & email client, running intrepid.
It has a Linksys WPC54G (PCMCIA) wireless adapter. The card works fine under WPA (PSK) on windoze, but the computer appeared to be struggling with the bloated OS, which is why I installed Linux.
I had the usual problems with Network Manager, so I replaced it with wicd.
I am using a static IP address, and have checked and re-checked the settings a dozen times.
The wired connection connects almost instantly, so I took the opportunity to upgrade everything.
Using the cutter, I have installed the b43legacy drivers for this card. It can now 'see' my wireless router (and my neighbour's...), but won't connect.
I have tried removing WPA. The adapter 'appears' to connect with the message:
"Connected to XXXX at 0% (IP: xxx.xxx.xxx.xxx)"
But I am unable to ping the router. :-(

Here is the output from lshw:
```

craig@Biggles:~$ sudo lshw -C network
  *-network               
       description: 802.11b CardBus
       vendor: Broadcom
       physical id: 0
       version: 8.0
       slot: Socket 0
       resources: irq:9
  *-network
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 51
       serial: 00:a0:cc:d5:2d:b5
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=half latency=32 link=no maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=10MB/s
  *-network
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:02:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:06:25:40:ea:93
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 9e:55:98:cc:a4:5b
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

iwconfig:
```

craig@Biggles:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"Scarlet"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

```

ifconfig:
```

craig@Biggles:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:a0:cc:d5:2d:b5  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:9 Base address:0xc700 

wlan0     Link encap:Ethernet  HWaddr 00:06:25:40:ea:93  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-06-25-40-EA-93-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

and iwlist:
```

craig@Biggles:~$ sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:11:50:A0:AC:DF
                    ESSID:"Belkin54g"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=38/100  Signal level:-80 dBm  Noise level=-59 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=0000035a5c055188
                    Extra: Last beacon: 5488ms ago
          Cell 02 - Address: 00:11:95:94:E4:52
                    ESSID:"Scarlet"
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=76/100  Signal level:-48 dBm  Noise level=-29 dBm
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:tsf=0000000fc93c40d5
                    Extra: Last beacon: 952ms ago

```

Any help or advice would be greatly appreciated.

TIA,
Craig

---

### Post by kevdog on 2009-01-04
Things look good from what you have presented.  Does dhcp work?  Have you tried troubleshooting your connection using the terminal instead of wicd to make a connection, or looked within wicd's logs to find any debugging output?  I have a link in my signature to use the terminal for network connections.  Additionally will connecting without any encryption on (no wpa) work?

---

### Post by rijidij on 2009-01-04
Hi kevdog,

Thanks for your reply.
I have disabled WPA, and enabled DHCP. Here are the results of the Unencrypted Connection section of your guide.

```

craig@Biggles:~$ sudo ifconfig wlan0 down
craig@Biggles:~$ sudo dhclient -r wlan0
There is already a pid file /var/run/dhclient.pid with pid 6630
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:06:25:40:ea:93
Sending on   LPF/wlan0/00:06:25:40:ea:93
Sending on   Socket/fallback
craig@Biggles:~$ sudo ifconfig wlan0 up
craig@Biggles:~$ sudo iwconfig wlan0 essid "Scarlet"
craig@Biggles:~$ sudo iwconfig wlan0 mode Managed
craig@Biggles:~$ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:06:25:40:ea:93
Sending on   LPF/wlan0/00:06:25:40:ea:93
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
craig@Biggles:~$

```

Still no joy :(

Regards,
Craig

---

### Post by rijidij on 2009-01-06
I've finally got this working.
After struggling with the native drivers for almost a week, I finally relented, removed the b43legacy drivers, and installed the ndiswrapped windoze driver.
A quick reboot, and wireless connected almost immediately.

Special thanks to kevdog for your help.

:)

---

### Post by kevdog on 2009-01-06
Thats disappointing that the b43 drivers didn't work for you.  I have the same card.  I used to use ndiswrapper all the time, but switched b/c I couldn't get ndiswrapper to work with WPA2 with Intrepid's kernel (although I could with Feisty, and Gutsy).

Glad you found a way.

---

### Post by rijidij on 2009-01-06
Yes, it is disappointing. I'm sure it must be possible, but it appears to be beyond my limited Linux skills.
I have spent far too much time on trying to make it work. I finally had to admit defeat.

Regards,
Craig

---

