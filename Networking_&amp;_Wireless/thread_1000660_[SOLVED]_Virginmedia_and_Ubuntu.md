---
title: "[SOLVED] Virginmedia and Ubuntu"
date: 2008-12-03
forum: Networking &amp; Wireless
---

### Post by spennyb on 2008-12-03
Hello All, THanks in advance for any replies.

I have just had virginmedia broadband installed which seems to work fine when booted into Vista but not in Ubuntu 8.10.

I am connected direct into a cable modem. eth0 gets an IP I can use nslookup and ftp from the command line which suggests all is ok. But I cant browse the web. every time I try to from firefox (No proxy setting) it just hangs and does not connect. It all works fine when connect to my wired work network.

I also get framing errors as follows which I dont get when connected to my work net...


spencerb@spencerb-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:09:3a:ad:95  
          inet addr:82.2.217.94  Bcast:82.2.219.255  Mask:255.255.252.0
          UP BROADCAST RUNNING MULTICAST  MTU:150  Metric:1
          RX packets:12 errors:40 dropped:0 overruns:0 frame:40
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1110 (1.1 KB)  TX bytes:2974 (2.9 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:242 errors:0 dropped:0 overruns:0 frame:0
          TX packets:242 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15140 (15.1 KB)  TX bytes:15140 (15.1 KB)

Routing table is as follows...

spencerb@spencerb-laptop:~$ netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
82.2.216.0      0.0.0.0         255.255.252.0   U         0 0          0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
0.0.0.0         82.2.216.1      0.0.0.0         UG        0 0          0 eth0
spencerb@spencerb-laptop:~$ netstat -r
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
82.2.216.0      *               255.255.252.0   U         0 0          0 eth0
link-local      *               255.255.0.0     U         0 0          0 eth0
default         cpc1-rdng4-0-0- 0.0.0.0         UG        0 0          0 eth0


nslookup......

spencerb@spencerb-laptop:~$ nslookup
> google.co.uk
Server:		194.168.4.100
Address:	194.168.4.100#53

Non-authoritative answer:
Name:	google.co.uk
Address: 72.14.221.104
Name:	google.co.uk
Address: 66.249.93.104
Name:	google.co.uk
Address: 216.239.59.104



ftp....

Connected
220 ** Welcome to FTP site **
Name (spencerb): 
Login failed.
ftp> quit
221 Goodbye.

For instance, when I browse...

Before...

spencerb@spencerb-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:09:3a:ad:95  
          inet addr:82.2.217.94  Bcast:82.2.219.255  Mask:255.255.252.0
          UP BROADCAST RUNNING MULTICAST  MTU:150  Metric:1
          RX packets:24 errors:43 dropped:0 overruns:0 frame:43
          TX packets:47 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2240 (2.2 KB)  TX bytes:4708 (4.7 KB)
          Interrupt:17 

After...

spencerb@spencerb-laptop:~$ start up f fox
start: Need to be root
spencerb@spencerb-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:09:3a:ad:95  
          inet addr:82.2.217.94  Bcast:82.2.219.255  Mask:255.255.252.0
          UP BROADCAST RUNNING MULTICAST  MTU:150  Metric:1
          RX packets:36 errors:65 dropped:0 overruns:0 frame:65
          TX packets:63 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3241 (3.2 KB)  TX bytes:6271 (6.2 KB)
          Interrupt:17 


I have not checked on vista if im getting errors as yet which and that its just handling them better. I will do when im back home.

THanks in advance for any help.

---

### Post by spennyb on 2008-12-03
Sorry forget to add my config...

Dell XPS M1330
Intel(R) Core(TM)2 Duo CPU     T7250  @ 2.00GHz
3GB RAM
250GB HDD
nVidia Corporation GeForce 8400M
Intel Corporation PRO/Wireless 3945ABG
Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express

Thx again, Spence.

---

### Post by spennyb on 2008-12-10
Hello all, Still seeing this problem. Any one have any ideas ??

It works fine on Opensolaris and Vista out of the box but for some reason not Ubuntu :( I have tried booting of the live CD and get the same results.

I know its not a MAC addr issue as its the same H/W and the OS is the same on all OS's i.e the OS is not doing anything weird with it.

From tcpdump/wireshark I see the following....


Frame 10 (114 bytes on wire, 96 bytes captured)
Ethernet II, Src: Dell, Dst: Cisco
Transmission Control Protocol, Src Port: 37110 (37110), Dst Port: http (80), Seq: 393, Ack: 1, Len: 48
Hypertext Transfer Protocol
[Packet size limited during capture: HTTP truncated]

Frame 11 (66 bytes on wire, 66 bytes captured)
Ethernet II, Src: Cisco, Dst: Dell
Transmission Control Protocol, Src Port: http (80), Dst Port: 37110 (37110), Seq: 1, Ack: 393, Len: 0

Frame 12 (114 bytes on wire, 96 bytes captured)
Ethernet II, Src: Dell, Dst: Cisco
Transmission Control Protocol, Src Port: 37110 (37110), Dst Port: http (80), Seq: 393, Ack: 1, Len: 48
Hypertext Transfer Protocol
[Packet size limited during capture: HTTP truncated]

Frame 13 (66 bytes on wire, 66 bytes captured)
Ethernet II, Src: Cisco, Dst: Dell
Transmission Control Protocol, Src Port: http (80), Dst Port: 37110 (37110), Seq: 977, Ack: 441, Len: 0

Any help is appreciated.

Thanks in advance,
Spence.

---

### Post by spennyb on 2008-12-15
Anyone have any ideas ?.

Thx again in advance,
Spence.

---

### Post by razy60 on 2008-12-15
How exactly are you connecting, what hardware, router, modem? via a server?

Raz

---

### Post by spennyb on 2008-12-15
Hi Raz,

Its basically a cat5 cable pluged direct into eth0 (RJ45 port) and into the back of the cable modem (RJ45 port). This modem is pluged into the the virgin media wall connection which was supplied and installed by virginmedia.

Its a weird one unless im missing something, strange that Open Solaris and Vista work fine out of the box and Ubuntu does no


Thanks again,
Spence.

---

### Post by razy60 on 2008-12-15
I take it you are using the virgin media modem(speedtouch), not a router.
In network manager is your ip address showing as 192.168.X.X(X being any number) how do the details compare to vista? ip address, dns etc, they should be the same.

Raz

---

### Post by spennyb on 2008-12-15
<removed as posted twice :) >

---

### Post by spennyb on 2008-12-15
Hi Raz


> I take it you are using the virgin media modem(speedtouch), not a router.

Thats right, its a new connection and I have not got round to buying a wireless router etc as yet.

>In network manager is your ip address showing as 192.168.X.X(X being any >number) how do the details compare to vista? ip address, dns etc, they >should be the same.

Its actually an 82.3.x.x addr which is got via DHCP. THis happends on Ubuntu, Solaris and Vista ok. And I am able to ftp/ping from all 3. Its basically just http stuff that seem broke on Ubuntu. I have checked my browser setting etc and all is ok.

If I disconnect from my home wired net and plug into my work wired net without rebooting etc so all setting are the same, it all works fine. Of course I get a diff DHCP addr here.

At home I seem to get packets like the following from tcpdump/wireshark...

Frame 10 (114 bytes on wire, 96 bytes captured)
Ethernet II, Src: Dell, Dst: Cisco
Transmission Control Protocol, Src Port: 37110 (37110), Dst Port: http (80), Seq: 393, Ack: 1, Len: 48
Hypertext Transfer Protocol
[Packet size limited during capture: HTTP truncated]

Frame 11 (66 bytes on wire, 66 bytes captured)
Ethernet II, Src: Cisco, Dst: Dell
Transmission Control Protocol, Src Port: http (80), Dst Port: 37110 (37110), Seq: 1, Ack: 393, Len: 0

and framing errors....

spencerb@spencerb-laptop:~$ ifconfig
eth0 Link encap:Ethernet HWaddr 00:1d:09:3a:ad:95
inet addr:82.3.N.9N Bcast:82.3.X.X Mask:255.255.252.0
UP BROADCAST RUNNING MULTICAST MTU:150 Metric:1
RX packets:24 errors:43 dropped:0 overruns:0 frame:43
TX packets:47 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:2240 (2.2 KB) TX bytes:4708 (4.7 KB)
Interrupt:17 

which I dont get under Solaris or Vista 


THanks again,
Spence who is confused.

---

### Post by razy60 on 2008-12-15
The only thing i can think of is that ubuntu has a problem with the modem, the reason being you can connect easy enough at work, i personally did not get on with it even on xp, it had a habit of trying to establish its own version of explorer which confused my pc so i had to disable the original i.e and allow virgin media's version as the default, they were no help as all they said was if you put in the supplied disc, etc.

found these 2 links may be of some use.
[http://www.linux-usb.org/SpeedTouch/](http://www.linux-usb.org/SpeedTouch/)
[http://ubuntuforums.org/showthread.php?t=969938](http://ubuntuforums.org/showthread.php?t=969938)

Raz

---

### Post by spennyb on 2008-12-15
Thanks Raz, It does look like Ubuntu out of the box has a problem with the modem. I thought this was the case because of the frame errors. I wondered if I need to change the out of the box setting to get it working but as of yet have not found what

Thanks for the links, I will have a read thru but one of them is for a USB modem and mine isnt one, er I think.

Spence.

---

### Post by razy60 on 2008-12-15
Have you looked at what your MTU settings are do they match, just an idea.


Raz

---

### Post by mick222 on 2008-12-15
just checked your settings against mine your mtu is only 150
> UP BROADCAST RUNNING MULTICAST MTU:150 Metric:1
mine is 1500 which is correct if you check this link it should help you change the mtu setting. [http://ubuntuforums.org/showthread.php?t=289077](http://ubuntuforums.org/showthread.php?t=289077)
my connection is just set to auto eth0 and automatic(dhcp) worked first time .

---

### Post by blazemore on 2008-12-15
Right-click on the network manager icon and do Connection Information. Is the DNS server showing as 194.168.4.100?

---

### Post by spennyb on 2008-12-17
Thanks very much for all your replies, manually changing the MTU to 1500 fixed it :)

Looks like this is not being set currently when eth0 gets the addr from DNS.

Thanks again,
Spence.

---

