---
title: "Still no internet over WiFi..."
date: 2009-03-07
forum: Networking &amp; Wireless
---

### Post by NewBeeMichael on 2009-03-07
Hi there,

However quite excited about my Ubuntu 8.10 system I ended up yesterday installing Ubuntu 8.10 Alternate CD instead of Ubuntu 8.10 Desktop on my Acer Aspire 1355LC laptop...

Sadly this gave me exact the same trouble I had before :(

I'm working with a Sweex WIRELESS LAN PC CARD 140 NITRO XM PCMCIA card (LW141) and a Sweex WIRELESS BROADBAND ROUTER 140 NITRO XM (LW140).

The actual problem is after installing ndiswrapper and loading the WinXP driver for the pcmcia card, the card is recognized and it even is 'seeing' the wireless networks in the neighboorhood, including my own. When selecting my network it tries to connect and asks for the WPA or WEP key (whatever is used). After entering this, a couple of seconds later is asks for the key again. It just doesn't connect!

When switching wireless security completely it seems to connect, however when entering a website in the address bar it stops again and I'm not even able to ping my router...

I've tried nearly everything mentioned on [https://help.ubuntu.com/8.10/internet/C/wireless.html](https://help.ubuntu.com/8.10/internet/C/wireless.html) and in the wireless troubleshooting section...

Does anyone have a bright idea how to get WiFi running?

Thanks!

Michael

---

### Post by Kalma on 2009-03-07
Though I am an absolute beginner too, it seems to me like a configuration problem...

Network key. Be sure you are writting exactly the same WPA (don't use WEP) Key in both, the router and the PC. To know the key your router is using, try to access it using no security or connecting it via Ethernet, then accessing its configuration page (typicaly at 192.268.1.1 or 192.168.0.1).

2-Times Key: When I introduced the Key, it requested me a second key, but this one was not related to the Network, but the password for the Key-Ring where Ubuntu will safely store the keys. Can this be the second key it is requesting?

Accessing Internet: You have to be sure you are setting the right parameters on the Network Configuration options. Write the correct SSID (you can leave blank the BSSID and the MAC), and chech System Default so your PC automatically starts that connection. Then set the Security Key and then the IPv4 settings. Try to force an static IP, this will allow you to set the GateWay (192.168.1.1, if so) and your ISP DNS (or, if you don't know, 192.168.1.1 again).

---

### Post by NewBeeMichael on 2009-03-07
Thanks Kalma for your reply,

With exactly the same data, the WiFi connection is working perfectly in WinXP. I do not even get to the point where I can access the routers page, before that the connection is gone again. I've checked all settings, and I am working by default with static IP's...

Connection over Ethernet there is no problem at all... it works perfectly! :D. Just the WiFi is giving problems at the moment...

Maybe some additional info: when restarting the PC, even the complete system gets stuck after trying to make a connection. The system can only be restarted with a 'hard' reset.

---

### Post by Kalma on 2009-03-07
Well, this really overwhelms me too... what a pair of "experts", don't you think? :-)

In case the connection works fine over Ethernet I would re-direct my attention to the WiFi Adapter driver... Are you sure you have the right one and the last version of it? You can see it by using

code:
lshw -C Network

---

### Post by NewBeeMichael on 2009-03-07
Haha, together we probably know a lot more than alone...;)

I will get you some outputs from the commands I learned the last days:

Funny is where is says ESSID off/any, that no WiFi network at all is mentioned

michael@Michael:~$ sudo lshw -C network 

*-network
description: Wireless interface
product: ISL3886 [Prism Javelin/Prism Xbow]
vendor: Intersil Corporation
physical id: 1
bus info: pci@0000:02:00.0
logical name: wlan0
version: 01
serial: xx:xx:xx:xx:xx
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=ndiswrapper+wlancig driverversion=1.53+Sweex Europe,02/16/2005, 3. latency=56 link=no maxlatency=28 mingnt=10 module=ndiswrapper multicast=yes wireless=IEEE 802.11g

michael@Michael:~$ sudo ifconfig
      
wlan0     
Link encap:Ethernet  
HWaddr 00:16:0a:00:65:49  
inet6 addr: fe80::216:aff:fe00:6549/64 
Scope:Link
UP BROADCAST MULTICAST  
MTU:1500  Metric:1 RX packets:13 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1661 (1.6 KB)  TX bytes:1920 (1.9 KB)
          Interrupt:5 Memory:34000000-34002000 

michael@Michael:~$ sudo iwconfig
wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.427 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:19 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by Kalma on 2009-03-07
For sure we do... and also bear in mind that the journey is what really minds.

Wel after the cafe-philosophy ;-) let's try to go on...

The driver is: driver=ndiswrapper+wlancig driverversion=1.53+Sweex Europe,02/16/2005, 3. I guess it's the one coming on your Window$ CD, right?

Another strange thing is your WiFi Adapter MAC, which seems to be null (serial: xxxxxx) If so, it seems like if Ubuntu has not "acquired" it. One thing just came up: how have you installed Ubuntu? I mean, have you open an Ubuntu window on your WinXP System? If so, I imagine that you can not use the same Wifi Adapter from two separate OS and it would generate conflicts...

Look mine:
-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:03:2f:33:7e:06
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+sis163u driverversion=1.53+OEM,11/29/2004,5.1.1039.102 ip=192.168.1.114 link=yes multicast=yes wireless=IEEE 802.11g

---

### Post by NewBeeMichael on 2009-03-07
The driver file is coming directly from Sweex, supplied on the website

The MAC address is shown correctly, just took it out and replaced by x's ;)

Ubuntu is running on it's own, I created a dual boot system with WinXP on one partition and Ubuntu on the other... so I would be surprised if Windows is still using the driver where it doesn't run :P

It seems to me that the driver is messing up the joy, but I'm not sure, because sometimes it seems to work, but in the end it doesn't. Meanwhile, I've also switched off the IPV6, but unfortunately no luck so far...

We'll keep on trying, it should be able to run fine, shouldn't it ?!

---

### Post by Kalma on 2009-03-07
Abso-f**ing-lutely it should!!!

One more thing (we have nothing to lose in the meantime). Can it be an USB conflict? Sometimes the USB is associated to another thing. Try this and see what it says

ced:
lsusb

Look mine:
Bus 005 Device 004: ID 0457:0163 Silicon Integrated Systems Corp. 802.11 Wireless LAN Adapter
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 15d9:0a33  
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

You can see the first one is properly associated to my WiFi Adapter...

Also here there is a guy who explains how to solve this kind of conflicts (though he's trying to set-up an USB modem, but the USB management is similar):
[http://www.todoultraportatiles.com/post908.html](http://www.todoultraportatiles.com/post908.html)

I have also found this page, related to the ndiswrapper management (some of these things are not included in the "official" tutorial, so maybe they can help):
[http://www.technetra.com/2004/07/27/wireless-networking-using-ndis-wrapper/](http://www.technetra.com/2004/07/27/wireless-networking-using-ndis-wrapper/)

---

### Post by NewBeeMichael on 2009-03-07
As I'm using a pcmcia card, there is no info at the usb section. Lucky me the card is also not mentioned here, so no conflicts so far.

The card is mentioned in the pci section and seems to be recognized without problems; its the last one 02:00.0. I can't dicover any conflicts between devices so far...:

michael@Michael:~$ sudo lsusb


Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub



michael@Michael:~$ sudo lspcmcia


Socket 0 Bridge:   	[yenta_cardbus] 	(bus ID: 0000:00:07.0)
  CardBus card -- see "lspci" for more information



michael@Michael:~$ sudo lspci


00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8235 PCI Bridge
00:07.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
00:08.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: VIA Technologies, Inc. KM400/KN400/P4M800 [S3 UniChrome] (rev 01)
02:00.0 Network controller: Intersil Corporation ISL3886 [Prism Javelin/Prism Xbow] (rev 01)

---

### Post by NewBeeMichael on 2009-03-08
Now I've tried to alter the menu.lst file and added the commands acpi=off, noapic nolapic, pci=noacpi and acpi=oldboot as described on [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)... With the first one it had connection at login so I was happily surprised!!! But... after opening FireFox and clicked the first link I came across the connection dropped again.

Also tried to blacklist common Linux drivers, but also this didn't give the expected result. The "Link" LED on my card is burning, but the "Act." LED doesn't burn at all (only for the very short time there is a connection established)

Anyone any ideas?? Thanks.

---

### Post by NewBeeMichael on 2009-03-14
Now this is the output after reinstalling NDISWRAPPER completely. Can anyone see something strange on the tail /var/log/messages part? These messages don't tell me anything to be honest ;-)


michael@Michael:~$ ndiswrapper -l
prisma00 : driver installed
	device (1260:3886) present (alternate driver: p54pci)

michael@Michael:~$ sudo depmod -a

michael@Michael:~$ sudo modprobe ndiswrapper

michael@Michael:~$ tail /var/log/messages
Mar 14 17:42:44 Michael kernel: [  176.271446] type=1503 audit(1237048964.924:5): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/5793/net/" pid=5793 profile="/usr/sbin/cupsd"
Mar 14 17:42:44 Michael kernel: [  176.275217] type=1503 audit(1237048964.928:6): operation="socket_create" family="ax25" sock_type="dgram" protocol=0 pid=5793 profile="/usr/sbin/cupsd"
Mar 14 17:42:44 Michael kernel: [  176.278163] type=1503 audit(1237048964.932:7): operation="socket_create" family="netrom" sock_type="seqpacket" protocol=0 pid=5793 profile="/usr/sbin/cupsd"
Mar 14 17:42:44 Michael kernel: [  176.281216] type=1503 audit(1237048964.936:8): operation="socket_create" family="rose" sock_type="dgram" protocol=0 pid=5793 profile="/usr/sbin/cupsd"
Mar 14 17:42:44 Michael kernel: [  176.284573] type=1503 audit(1237048964.940:9): operation="socket_create" family="ipx" sock_type="dgram" protocol=0 pid=5793 profile="/usr/sbin/cupsd"
Mar 14 17:42:44 Michael kernel: [  176.284591] type=1503 audit(1237048964.940:10): operation="socket_create" family="appletalk" sock_type="dgram" protocol=0 pid=5793 profile="/usr/sbin/cupsd"
Mar 14 17:42:44 Michael kernel: [  176.284604] type=1503 audit(1237048964.940:11): operation="socket_create" family="econet" sock_type="dgram" protocol=0 pid=5793 profile="/usr/sbin/cupsd"
Mar 14 17:42:44 Michael kernel: [  176.284615] type=1503 audit(1237048964.940:12): operation="socket_create" family="ash" sock_type="dgram" protocol=0 pid=5793 profile="/usr/sbin/cupsd"
Mar 14 17:42:44 Michael kernel: [  176.284625] type=1503 audit(1237048964.940:13): operation="socket_create" family="x25" sock_type="seqpacket" protocol=0 pid=5793 profile="/usr/sbin/cupsd"
Mar 14 17:42:44 Michael kernel: [  176.284715] type=1503 audit(1237048964.940:14): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=7 name="/proc/5793/net/dev" pid=5793 profile="/usr/sbin/cupsd"

---

### Post by NewBeeMichael on 2009-03-15
OK, this is what I found out from the system log, it might clarify for some of you what happends... Furthermore the complete log is filled with the same message: "phy0: tx overflow".

Any advice would be appreciated...

Mar 15 17:03:44 Michael kernel: [  139.265912] phy0: tx overflow.
Mar 15 17:03:44 Michael kernel: [  139.265918] phy0: tx overflow.
Mar 15 17:03:48 Michael kernel: [  142.360684] type=1503 audit(1237133027.996:5): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/5669/net/" pid=5669 profile="/usr/sbin/cupsd"
Mar 15 17:03:48 Michael kernel: [  142.364545] type=1503 audit(1237133028.000:6): operation="socket_create" family="ax25" sock_type="dgram" protocol=0 pid=5669 profile="/usr/sbin/cupsd"
Mar 15 17:03:48 Michael kernel: [  142.367641] type=1503 audit(1237133028.000:7): operation="socket_create" family="netrom" sock_type="seqpacket" protocol=0 pid=5669 profile="/usr/sbin/cupsd"
Mar 15 17:03:48 Michael kernel: [  142.370710] type=1503 audit(1237133028.004:8): operation="socket_create" family="rose" sock_type="dgram" protocol=0 pid=5669 profile="/usr/sbin/cupsd"
Mar 15 17:03:48 Michael kernel: [  142.373600] type=1503 audit(1237133028.008:9): operation="socket_create" family="ipx" sock_type="dgram" protocol=0 pid=5669 profile="/usr/sbin/cupsd"
Mar 15 17:03:48 Michael kernel: [  142.373617] type=1503 audit(1237133028.008:10): operation="socket_create" family="appletalk" sock_type="dgram" protocol=0 pid=5669 profile="/usr/sbin/cupsd"
Mar 15 17:03:48 Michael kernel: [  142.373629] type=1503 audit(1237133028.008:11): operation="socket_create" family="econet" sock_type="dgram" protocol=0 pid=5669 profile="/usr/sbin/cupsd"
Mar 15 17:03:48 Michael kernel: [  142.373640] type=1503 audit(1237133028.008:12): operation="socket_create" family="ash" sock_type="dgram" protocol=0 pid=5669 profile="/usr/sbin/cupsd"
Mar 15 17:03:48 Michael kernel: [  142.373650] type=1503 audit(1237133028.008:13): operation="socket_create" family="x25" sock_type="seqpacket" protocol=0 pid=5669 profile="/usr/sbin/cupsd"
Mar 15 17:03:48 Michael kernel: [  142.373744] type=1503 audit(1237133028.008:14): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=7 name="/proc/5669/net/dev" pid=5669 profile="/usr/sbin/cupsd"
Mar 15 17:03:49 Michael kernel: [  143.757105] phy0: tx overflow.
Mar 15 17:03:49 Michael kernel: [  143.784133] phy0: tx overflow.


Mar 15 17:02:22 Michael pulseaudio[5390]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Mar 15 17:02:53 Michael kernel: [   87.784056] pccard: CardBus card inserted into slot 0
Mar 15 17:02:53 Michael kernel: [   87.784183] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Mar 15 17:02:53 Michael kernel: [   87.784191] pci 0000:02:00.0: PME# disabled
Mar 15 17:02:53 Michael kernel: [   88.176182] prism54pci 0000:02:00.0: enabling device (0000 -> 0002)
Mar 15 17:02:53 Michael kernel: [   88.178051] prism54pci 0000:02:00.0: PCI INT A -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5
Mar 15 17:02:53 Michael kernel: [   88.231407] firmware: requesting isl3886
Mar 15 17:02:53 Michael kernel: [   88.301221] p54: LM86 firmware
Mar 15 17:02:53 Michael kernel: [   88.301234] p54: FW rev 2.7.0.0 - Softmac protocol 4.1
Mar 15 17:02:54 Michael kernel: [   89.221851] p54: unknown eeprom code : 0x1
Mar 15 17:02:54 Michael kernel: [   89.221863] p54: unknown eeprom code : 0x3
Mar 15 17:02:54 Michael kernel: [   89.221867] p54: unknown eeprom code : 0x1905
Mar 15 17:02:54 Michael kernel: [   89.221876] p54: unknown eeprom code : 0x1007
Mar 15 17:02:54 Michael kernel: [   89.221879] p54: unknown eeprom code : 0x1008
Mar 15 17:02:54 Michael kernel: [   89.221882] p54: unknown eeprom code : 0x1100
Mar 15 17:02:55 Michael kernel: [   89.493722] phy0: hwaddr 00:16:0a:00:65:49, isl3886
Mar 15 17:02:59 Michael kernel: [   93.622216] firmware: requesting isl3886
Mar 15 17:02:59 Michael kernel: [   93.638855] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Mar 15 17:02:59 Michael kernel: [   93.734617] NET: Registered protocol family 17
Mar 15 17:03:30 Michael kernel: [  124.596054] phy0: tx overflow.
Mar 15 17:03:30 Michael kernel: [  124.596074] phy0: tx overflow.
Mar 15 17:03:30 Michael kernel: [  124.656067] phy0: tx overflow.

---

### Post by dorpm on 2009-05-04
The reason might be the same as described here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/363528](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/363528)

Regards,
Florian

---

