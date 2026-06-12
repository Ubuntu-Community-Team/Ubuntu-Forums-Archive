---
title: "Please help me with this problem!"
date: 2011-08-04
forum: Networking &amp; Wireless
---

### Post by Hubie1000 on 2011-08-04
okay so this is my very first post and i know that all of you linux users out there (ubuntu/kubuntu/xubuntu/ect.) are more savvy to a noob like me, i have been using ubuntu for just over 3 months now and i completely love it. but heres where the problem starts (and please let me know if i am in the right topic) i recently installed ubuntu 10.10 on my roommates computer, the reason being is that the IT department here on college "fixed it" for him, now it wont connect to the internet. it will however connect if we use an ethernet cable from the other laptop to his. his had originally windows xp then got upgraded to vista. i was wondering if there was a way to completely reset the networking wifi card if that might be the problem. any help would be appreciated.

my roommates computer is a DakTech PlaidBook, however i do not know on how to check the system information in the terminal to tell you what wifi card he has and such, all i want is to have internet back on his computer again. 

again any help would be greatly appreciated. :P

---

### Post by JC Cheloven on 2011-08-04
Hi, and welcome to the forums.
So, the problem is that wifi doesn't work? (sorry I got a bit lost through the explanation, I'm getting old for sure). We need a little more specific info.

First thing would be to know whether your wifi card is recognised and working. When you click on the network manager icon, does some wifi networks appear? Also, what's the output when you type at a terminal each of these commands```
ifconfig
``````
lspci
```
Note you can copy from the terminal selecting with the mouse and using the function in the edit menu. 

> had originally windows xp then got upgraded to vista-> This can hardly be called an "upgrade" LOL

---

### Post by Hubie1000 on 2011-08-04
thats the problem, it says it can identify networks, it just wont connect to them. Thats all thanks to the brilliant IT department here on campus. as for your suggestion, i totally agree from xp to vista can hardly be called an upgrade, i think i did him a favor :D

to your reply of the codes--(i have to type this all out on my computer so it might not look the way it should)

as for the ifconfig command----

eth0

Link encap: Etherenet HWaddr 00:26:22:27:f7:1e
inet6 addr: fe80::226:22ff:fe27:f71e/64 Scope:Link
UP BROADCAST MULTICAST    MTU:1500 Metric:1
RX packets:6353312 errors:0 dropped:0 overruns:0 frame:0
TX packets:2340116 errors:0 dropped:0 overruns:0 carrier:0
collistions:0 txqueuelen:1000
RX bytes:1856616890 (1.8 GB)   TX bytes:189182286 (189.1 MB)
Interrupt:29 Base address : 0xa000

lo

Link encap: Local Loopback
inet addr:127.0.01   Mask:255.0.0.0
inet6 addr:   ::1/128 Scope:Host
UP LOOPBACK RUNNING    MTU:16436   Metric:1
RX packets:33563 errors:0 dropped:0 overruns:0 frame:0
TX packets:33563 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:2630744 (2.6 MB)    TX bytes:2630744  (2.6 MB)

wlan0

Link encap:Ethernet   HWaddr 00:1e:65:a3:4c:14
inet6 addr:  fec0::b:21e:65ff:fea3:4c14/64  Scope:Site
inet6 addr:  2002:8681:2df2:b:21e:65ff:fea3:fc14/64  Scope:Global
inet6 addr:  fe80::21e:65ff: fea3:4c14/64  Scope:Link
UP BROADCAST MULTICAST   MTU:1500   Metric:1
RX packets:38708 errors:0 dropped:0 overruns:0 frame:0
TX packets:242 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:3906576  (3.9 MB)   TX bytes:52671  (52.6 KB)


as for the lspci command----


00:00.0  Host bridge:   Intel Corporation Mobile 4 Series Chipset Memory Controller
 Hub (rev 07)
00:02.0 VGA compatible controller:   Intel Corporation Mobile 4 Series Chipset Int
egraded Graphics controller (rev 07)
00:02.1 Display controller:   Intel Corporation Mobile 4 Series Chipset Integrated
 Graphics controller (rev 07)
00:1a.0 USB Controller:   Intel Corporation 82801I (ICH9 Family) USB UHCI Controll
er #4 (rev 03)
00:1a.1 USB Controller:   Intel Corporation 82801I (ICH9 Family) USB UHCI Controll
er #5 (rev 03) 
00:1a.7 USB Controller:  Intel Corporation 82801I (ICH9 Family) USB2 EHCI Control
ler #2 (rev 03)
00:1b.0 Audio device:   Intel Corporation 82801I (ICH9 Family) HD Audo Controller
 (rev 03)
00:1c.0 PCI bridge:   Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (r
ev 03)
00:1c.1 PCI bridge:   Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (r
ev 03)
00:1c.2 PCI bridge:   Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (r
ev 03)
00:1c.3 PCI bridge:   Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (r
ev 03)
00:1c.4 PCI bridge:   Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (r
ev 03)
00:1d.0 USB Controller:   Intel Corporation 82801I (ICH9 Family) USB UHCI Controll
er #1 (rev 03)
00:1d.1 USB Controller:   Intel Corporation 82801I (ICH9 Family) USB UHCI Controll
er #2 (rev 03)
00:1d.2 USB Controller:   Intel Corporation 82801I (ICH9 Family) USB UHCI Controll
er #3 (rev 03)
00:1d.7 USB Controller:   Intel Corporation 82801I (ICH9 Family) USB UHCI Controll
er #1 (rev 03)
00:1f.3 SMBus:   Intell Corporation 82801I (ICH9 Family) SMBus controller (rev 03)
00:1f.5 IDE interface:   Intel Corporation ICH9M/M-E port SATA IDE Controller (r
ev 03)
0e:00.0 Network controller:   Intel Corporation Wireless WiFi Link 5100
14:00.0 Ethernet controller:   Realteck Semiconductor Co., Ltd. RTL8101E/RTL8102E P
CI Express Fast Ethernet conroller (rev 02)
1a:00.0 System peripheral:   JMicron Technology Corp. SD/MMC Host Controller
1a:00.2 SD Host conroller:   JMicron Technology Corp. Standard SD Host Controller
1a:00.3 System peripheral:   JMicron Technology Corp. MS Host Controller
1a:00.4 System peripheral:   JMicron Technology Corp. xD Host Controller


end codes


that is what i got when i put the codes into the terminal, hope it was what you were looking for :)

---

### Post by Furball588 on 2011-08-04
Might not be a bad idea to do ifconfig on yours and compare.. :)  Looks like it only wants to talk at IPv6

Try running sudo dhclient eth0 in a terminal and look at ifconfig again.

---

### Post by Hubie1000 on 2011-08-04
your talkin on his computer right?

---

### Post by Furball588 on 2011-08-04
> **Hubie1000 said:**
> your talkin on his computer right?

yes, for the dhclient command.  

Yours for ifconfig.  You don't need to if you don't want, but since yours is working, it might not be a bad idea for you to see how yours is setup and his is....or did I mis-read that you're both running ubuntu...

---

### Post by Hubie1000 on 2011-08-04
when i put in the sudo dhclient eth0 command i got (in his computer)


Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet System Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/eth0/00:26:22:27:f7:1e
Sending on LPF/eth0/00:26:22:27:f7:1e
Sending on Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
No DHCCPOFFERS recieved.
No working leases in persistent database - sleeping.


ill have to check the differrence between the ifconfig lines after i get back onto the forum

---

### Post by Hubie1000 on 2011-08-04
no you didnt misread it, we are both running ubuntu 10.10 and my ifconfig lines look way different than his does.

---

### Post by Hubie1000 on 2011-08-04
the only difference that i seen in the ifconfig on his computer after the sudo command was the RX and TX bytes were different, still no internet connection.

---

### Post by Furball588 on 2011-08-04
> **Hubie1000 said:**
> No DHCCPOFFERS recieved.

Either their DHCP service is down, they're not willing to offer him a lease, or the ethernet is unplugged?

---

### Post by Hubie1000 on 2011-08-05
i currently do not have it connected by ethernet no, but what i am looking for is to try to get his wifi going again, thats why i was wondering if like a new ip address or completely reseting his wifi card or networking card or whatever might do the trick. 

like i said before im just trying to get it to connect back with its wifi, as i do not know what the IT department did to his computer.

---

### Post by Furball588 on 2011-08-05
> **Hubie1000 said:**
> i currently do not have it connected by ethernet no, but what i am looking for is to try to get his wifi going again, thats why i was wondering if like a new ip address or completely reseting his wifi card or networking card or whatever might do the trick. 

like i said before im just trying to get it to connect back with its wifi, as i do not know what the IT department did to his computer.

oh sorry...I thought we were working with ethernet...

Then I guess sudo dhclient wlan0  Hopefully pulling a new lease will give you the items you need to authenticate if you need to...

It looks like you're wireless device is configured...the question is why isn't it seeing the wireless network there..

---

### Post by Hubie1000 on 2011-08-05
and thats what i need help with, it just wont connect. :(

---

### Post by Hubie1000 on 2011-08-05
when i did the sudo dhclient wlan0 this is what came up:

There is already a pid file /var/run/dhclient.pid with pid 14953
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.3
Copryright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/softwar/dhcp](https://www.isc.org/softwar/dhcp)

Listening on LPF/wlan0/00:1e:65:a3:4c:14
Sending on LPF/wlan0/00:1e:65:a3:4c:14
Sending on Socket/fallback
DHCPDISCOVER on wlan0 to255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to255.255.255 port 67 interval 8
No DHCPDISCOVER recieved.
No working leases in persistent database - sleeping.





thats what i go, it still didnt connect :-(

---

### Post by Furball588 on 2011-08-05
I'd say give this thread a read

[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

I'm believing your interface is loaded as it should.  It's just a matter of getting it to at least challenge for passkey or something...

---

