---
title: "Toshiba A355D, Atheros AR928X wifi, Ubuntu 8.10"
date: 2008-12-22
forum: Networking &amp; Wireless
---

### Post by jdrago_999 on 2008-12-22
I installed Ubuntu 8.10 on my new Toshiba A355D-S6885 a couple days ago and I'm trying to get the wifi working on it.

BTW - everything else works just fine (graphics, ethernet, sound, etc).

The ath9k drivers were installed during the setup process, and the network card appears to be detected.  However, when I try to connect to my wireless router, nothing happens.

Down to details, here we go:
```
john@ubuntu-laptop:~/Desktop$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Toshiba America Info Systems Device 9602
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780MC [Radeon HD 3100 Graphics]
08:00.0 FireWire (IEEE 1394): JMicron Technologies, Inc. IEEE 1394 Host Controller
08:00.1 System peripheral: JMicron Technologies, Inc. SD/MMC Host Controller
08:00.2 SD Host controller: JMicron Technologies, Inc. Standard SD Host Controller
08:00.3 System peripheral: JMicron Technologies, Inc. MS Host Controller
08:00.4 System peripheral: JMicron Technologies, Inc. xD Host Controller
0e:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
14:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
```

```
john@ubuntu-laptop:~/Desktop$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:ec:40:9d:02  
          inet addr:192.168.2.2  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:ecff:fe40:9d02/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:50219 errors:0 dropped:313498628 overruns:0 frame:0
          TX packets:55364 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:38618253 (38.6 MB)  TX bytes:7685208 (7.6 MB)
          Interrupt:219 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:154 errors:0 dropped:0 overruns:0 frame:0
          TX packets:154 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:12268 (12.2 KB)  TX bytes:12268 (12.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:21:63:75:a9:a1  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:107 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6597 (6.5 KB)  TX bytes:5452 (5.4 KB)

wlan0:avahi Link encap:Ethernet  HWaddr 00:21:63:75:a9:a1  
          inet addr:169.254.8.16  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

wmaster0  Link encap:UNSPEC  HWaddr 00-21-63-75-A9-A1-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```





```
john@ubuntu-laptop:~/Desktop$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"Andromeda"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=23 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.
```


sudo lspci -v:
```
0e:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
	Subsystem: Askey Computer Corp. Device 7136
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at f0200000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: [40] Power Management version 2
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Capabilities: [60] Express Legacy Endpoint, MSI 00
	Capabilities: [90] MSI-X: Enable- Mask- TabSize=1
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [140] Virtual Channel <?>
	Capabilities: [160] Device Serial Number 00-00-00-00-00-00-00-00
	Kernel driver in use: ath9k
	Kernel modules: ath9k

```

The router is using WEP 64-bit encryption.

I also have tried with the following shell script:
```
#!/bin/sh

sudo ifconfig wlan0 down
sudo dhclient -r wlan0
sudo ifconfig wlan0 up
sudo route add default gw 192.168.0.1 wlan0
sudo iwconfig wlan0 essid "Andromeda"
sudo iwconfig wlan0 key d7eff3f108
sudo iwconfig wlan0 enc d7eff3f108
sudo iwconfig wlan0 mode Managed
sudo iwconfig wlan0 channel 6
#sudo iwconfig wlan0 ap "00:17:3F:BF:D9:F6"
sudo dhclient wlan0
```

When I run the above script, I get the following output (from dhclient I suppose):
```
There is already a pid file /var/run/dhclient.pid with pid 20240
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:21:63:75:a9:a1
Sending on   LPF/wlan0/00:21:63:75:a9:a1
Sending on   Socket/fallback
SIOCADDRT: No such process
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:21:63:75:a9:a1
Sending on   LPF/wlan0/00:21:63:75:a9:a1
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

The log on my router shows no activity at all during the whole process.

I saw another post here regarding the same wifi card, but the solution there won't work for this one (the other thread involved turning off bluetooth, which this laptop does not have).

Any ideas?

---

### Post by jdrago_999 on 2008-12-22
One more thing:

When I first boot up, NetworkManager appears to have connected to the wifi (even says that it has connected to "Andromeda" - the ssid).

However, if I pull the network cable from my laptop, I can't ping anything or go anywhere.

However, while in that connected-but-not-really state, I ran the following commands:
```
john@ubuntu-laptop:~$ ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:21:63:75:a9:a1  
          inet addr:192.168.2.3  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::221:63ff:fe75:a9a1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:34 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3342 (3.3 KB)  TX bytes:5341 (5.3 KB)

john@ubuntu-laptop:~$ iwconfig wlan0
wlan0     IEEE 802.11abgn  ESSID:"Andromeda"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:17:3F:BF:D9:F5   
          Bit Rate=1 Mb/s   Tx-Power=23 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=101/100  Signal level:-30 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```


Hope this helps someone help me :)

---

### Post by jdrago_999 on 2008-12-22
bump?

---

### Post by superprash2003 on 2008-12-23
post output of ping 192.168.2.1 from the terminal... presuming its your wifi router ip..

---

### Post by jdrago_999 on 2008-12-23
Thanks for your reply.

I just tried connecting again after a fresh reboot and got this:

```
john@ubuntu-laptop:~/Desktop$ ./wifi-connect 
[sudo] password for john: 
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:21:63:75:a9:a1
Sending on   LPF/wlan0/00:21:63:75:a9:a1
Sending on   Socket/fallback
SIOCADDRT: No such process
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:21:63:75:a9:a1
Sending on   LPF/wlan0/00:21:63:75:a9:a1
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPOFFER of 192.168.2.4 from 192.168.2.1
DHCPREQUEST of 192.168.2.4 on wlan0 to 255.255.255.255 port 67
DHCPACK of 192.168.2.4 from 192.168.2.1
SIOCADDRT: File exists
bound to 192.168.2.4 -- renewal in 917430888 seconds.
```

(This is the contents of "wifi-connect"):

```
#!/bin/sh

sudo ifconfig wlan0 down
sudo dhclient -r wlan0
sudo ifconfig wlan0 up
sudo route add default gw 192.168.0.1 wlan0
sudo iwconfig wlan0 essid "Andromeda"
sudo iwconfig wlan0 key [1] d7eff3f108
sudo iwconfig wlan0 mode Managed
sudo iwconfig wlan0 channel 4
sudo iwconfig wlan0 ap "00:17:3F:BF:D9:F6"
sudo dhclient wlan0
```


However, after that I tried pinging that IP and got this:

```
john@ubuntu-laptop:~/Desktop$ ping 192.168.2.1
PING 192.168.2.1 (192.168.2.1) 56(84) bytes of data.
^C
--- 192.168.2.1 ping statistics ---
95 packets transmitted, 0 received, 100% packet loss, time 94125ms
```

Also, the little "Wireless" icon on my router lit up, like it does when someone connects to it via wifi (nobody else could have connected - only me).

What now?

Thanks for your help :)

(Edit: Added the contents of "wifi-connect")

---

### Post by jdrago_999 on 2008-12-23
FYI I also mailed the ath9k developer's mailing list.

"Luis" over there suggested I try installing "linux-backports-modules-intrepid" (which I went ahead and tried).

After I did that, I noticed that the output of "sudo iwlist wlan0 scan" changed from this:

```
john@ubuntu-laptop:~/Desktop$ sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:17:3F:BF:D9:F5
                    ESSID:"Andromeda"
                    Mode:Master
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=31/100  Signal level:-75 dBm  Noise level=-95 dBm
                    Encryption key:on
                    IE: Unknown: 2D1AEE1115FFFF0000010000000000000000000000000E0000000000
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 12 Mb/s
                              24 Mb/s; 48 Mb/s
                    Extra:tsf=000000013501a3cc
                    Extra: Last beacon: 3424ms ago
```

To this:

```
john@ubuntu-laptop:~/Desktop$ sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:17:3F:BF:D9:F5
                    ESSID:"Andromeda"
                    Mode:Master
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=21/100  Signal level:-81 dBm  Noise level=-95 dBm
                    Encryption key:on
                    IE: Unknown: 0009416E64726F6D656461
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030104
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1AEE1115FFFF0000010000000000000000000000000E0000000000
                    IE: Unknown: 3D1604050000000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 7F0101
                    IE: Unknown: DD9D0050F204104A00011010440001021041000100103B000103104700100000000000000001100000173FBFD9F51021001242656C6B696E20436F72706F726174696F6E10230009463544383233332D3410240007312E30312E31351042000E31323732323832333333373133371054000800060050F20400011011001B42656C6B696E20576972656C65737320526F757465722857464129100800020004
                    IE: Unknown: DD07000C4304000000
                    IE: Unknown: 0706555320010B10
                    IE: Unknown: DD1E00904C33EE1115FFFF0000010000000000000000000000000E0000000000
                    IE: Unknown: DD1A00904C3404050000000000000000000000000000000000000000
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 12 Mb/s
                              24 Mb/s; 48 Mb/s
                    Extra:tsf=0000000c00184c7a
                    Extra: Last beacon: 912ms ago
```

Other than that, I haven't noticed any change.  Still can't connect.

Any other ideas?

---

### Post by superprash2003 on 2008-12-24
why have you set gateway to 192.168.0.1 when your router ip is 192.168.2.1 .. try changing that..

---

### Post by jdrago_999 on 2008-12-30
I reverted everything back to its original state, and voila - it just worked (sort of).

After first booting up, it would connect to my wifi, but DNS resolved very slowly.  Some kind of KDE tool showed an awful lot of DNS requests for the same domain before it actually resolved.  Then after a few minutes, my connection would drop and I could not reconnect.

This was with NetworkManager and with wicd and command-line.

I'm a programmer, not a network guy.  Frankly I am very annoyed that laptop support (while much better than a few years ago) is still so lacking.  I think one of these distributions needs to get this problem with the manufacturers worked out soon.  With the steaming pile that is Vista, and the 2x-3x overpriced Mac laptops on the market, the desktop market is being handed to Linux on a silver platter.

Carpe diem!

My solution?  I returned that Toshiba and picked up a Lenovo Y530 Ideapad at Fry's for the same price.  This one came with Intel wireless and everything Just Works.  Except the sound is goofy in Skype.  Oh well, sound was goofy on the Toshiba as well.

I'll ask a new question in the audio forum :)

Thanks for your help.

---

