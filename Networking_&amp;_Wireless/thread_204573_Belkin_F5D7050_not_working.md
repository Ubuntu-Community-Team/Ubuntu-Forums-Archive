---
title: "Belkin F5D7050 not working"
date: 2006-06-27
forum: Networking &amp; Wireless
---

### Post by luxerama on 2006-06-27
I'm sorry that I have to bother you guys again about a wireless problem but I just don't know what more I can do.

About my problem:
I have a Belkin USB dongle (Ralink rt2500usb chipset), which was recognised by Ubuntu and assigned to rausb0. both ifconfig and iwconfig get the device and give the following output:

ifconfig:
 	```

Link encap:Ethernet  HWaddr 00:11:50:8A:F4:EF
inet6 addr: fe80::211:50ff:fe8a:f4ef/64 Scope:Link
UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
```

iwconfig:
 	```

IEEE 802.11g  ESSID:off/any
Mode:Auto  Frequency:2.412 GHz  Access Point: Not-Associated
Bit Rate:11 Mb/s   Tx-Power:20 dBm   Sensitivity=-121 dBm
RTS thr:2347 B   Fragment thr:2346 B
Encryption key:off
Power Management:off
Link Quality:0  Signal level:0  Noise level:0
Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

When i try to configure the dongle with the network settings tool which is under Sytem>Administration it freezes as soon as it tries to activate the device. Additionally I installed Wifi-Radar but without luck it finds my wireless network but it doesn't connect. It only seems to scan eth0, sit0 and lo:

```

lo      Interface doesn't support scanning.
eth0  Interface doesn't support scanning.
sit0   Interface doesn't support scanning.
lo      no wireless extensions.
eth0  no wireless extensions.
sit0   no wireless extensions.

```

When I press connect it outputs the following:

	```

Error : unrecognised wireless request "ThePenguinNet"
Stale pid file.  Removing
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)
SIOCSIFADDR: No such device
inet: ERROR while getting interface flags: No such device
inet: ERROR while getting interface flags: No such device
Bind socket to interface: No such device

```
When I try sudo ifup it outputs the following:
	```

Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/wlan0/00:11:50:8a:f4:ef
Sending on   LPF/wlan0/00:11:50:8a:f4:ef
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database &#8211; sleeping.
```

I installed ndiswrapper installation tool added the windows driver, blacklisted the rt2500 module and tried it this way. All that did was change the name from rausb0 to wlan0.

Please anyone I am close to giving up. Thank in advance.

Ps. I had the same dongle working on Suse 10.0

---

### Post by JTC2006 on 2006-06-27
Hi,

I hope someone can help as I also have a Belkin F5D7050 and cannot get it to activate n Network Settings

Mine also freezes as soon as you hit the activate button

Thanks in advance if anyone has any ideas

Jim

---

### Post by luxerama on 2006-06-28
I thoguht I had a pretty good look around this forum to insure there is no post solving the same problem that I have encountered but Ive just come across one that might solve it. I do not have access to my Ubuntu machine to test whether it is working but it sounds like it will. The link to the thread: [http://www.ubuntuforums.org/showthread.php?t=187999](http://www.ubuntuforums.org/showthread.php?t=187999)
I will post again once I know whether it does the job or not. :-\"

---

### Post by JTC2006 on 2006-06-28
Hi Lux,

I'm up and running........  just. 

Here;s what I did and I hope it works for you as we seemed to have the same problem.  

Shutdown PC and remove Belkin USB Card 
Start Ubuntu and go to Network Setting, ensure no refderence to the card exists there.

Shutdown again, install card, restart Ubunto.  Go back to Network Settings.

Now immediately activate wireless connection wothout changing any of the defaults then press OK.  It should work ok. now restart and go back into network settings to ensure the card is still activated.  Now you can change any settings you like and Add network key etc.  Everything will work fine AS LONG AS YOU DONT ASSIGN A STATIC IP ADDRESS

Leave it as DHCP and life shuld be sweet.  I'm using Ubuntu 6.06 with Belkin USB card right now with the default driver and it's as sweet as can be.  I can't believe how responsive this is compared to XP.

I'm VERY new to Linux, but this seems great. I cant wait to get it all up and running the way I want

I hope this works for you too.

Jim

---

### Post by luxerama on 2006-06-29
Nope that doesnt work for me. Im now sharing the Internet with my Kubuntu box, Kubuntu seems to have no trouble at all recognising the card. Thanks anyway..........

---

### Post by luxerama on 2006-06-30
Well I think i found a new "workaround" for this problem.
First I disabled the wifi device with the gui, after disabling it, changes can be made to the setting without freezing afterwards. After the changes have been confirmed do not activate the device via the gui, open up the console and do sudo ifup deviceid.
Works fine now.

---

