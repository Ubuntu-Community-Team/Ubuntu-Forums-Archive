---
title: "Wired DSL connection dropped (&quot;No network connection&quot;)"
date: 2009-04-01
forum: Networking &amp; Wireless
---

### Post by chicory on 2009-04-01
Yesterday I have installed Ubuntu on Dell Inspiron 9300 laptop.
Previously the laptop was running Windows XP and I have not experienced any networking issues. On Ubuntu, Internet worked perfectly fine for the first 6-8 hours and then suddenly the connection was dropped as I was browsing and I was unable to get it back since. I have even tried to reinstall Ubuntu from scratch, but that didn't help.

This a DSL wired connection via Linksys WRV54G router.
There are 3 other systems plugged into the router (Two Windows XP systems and one Debian 5.0). None of them experience any problems. The cable is fine - I plugged it to another computer to check. 

This is an Automatic Configuration DHCP connection.

Laptop uses Belkin PCMCIA Notebook Network Card (F5D5020).

I've searched the forums, but couldn't get a solution.
Here are some things which seem to be often requested by the forum community. Hope this helps:

```

holli@holli-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:12:3f:dc:16:0c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

eth1      Link encap:Ethernet  HWaddr 00:12:f0:ac:bf:0a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Base address:0x6000 Memory:dfcfd000-dfcfdfff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:264 errors:0 dropped:0 overruns:0 frame:0
          TX packets:264 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:17368 (17.3 KB)  TX bytes:17368 (17.3 KB)

```

```

holli@holli-laptop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

```

```

holli@holli-laptop:~$ ping 74.125.67.100
connect: Network is unreachable
holli@holli-laptop:~$ 

```

FYI:
I am very much a newbie in networking AND in Linux, so please keep this in mind...

Thank you!

---

### Post by chicory on 2009-04-02
Bump...

I am still right there where I was. Since yesterday I have tried dozens of things, including setting up static IP, but with no results. I am suspecting that it might be a Network Card issue, but I am not 100% sure.

Also, as an FYI: I have tried editing /etc/pcmcia/config.opts and adding the following lines:
```

card "Belkin-5020"
version "Belkin" , "F5D5020-PCMCIA-Network-Card"
bind "pcnet_cs"

```

There were zero results - still no wired connection. (I got a wireless connection no problem) 
I have reinstalled Ubuntu again and it's once again a clean slate now - ready to try anything you would kindly suggest.

---

### Post by superprash2003 on 2009-04-02
**any idea if eth0 or eth1 is connected to the network? . in your terminal type **sudo dhclient eth0 . also type** sudo dhclient eth1** and post output

---

### Post by chicory on 2009-04-02
> **superprash2003 said:**
> **any idea if eth0 or eth1 is connected to the network? . in your terminal type **sudo dhclient eth0 . also type** sudo dhclient eth1** and post output

Thank you for your reply!

I might be wrong, but I believe eth0 is my wired and eth1 is my wireless connection. 

Wireless is what I am currently using. I can connect to my neighbor's network and to my linksys wireless router network as well (the same very Router that the inoperable wired network is connected to). Currently I am connected to my neighbor's network. 

Here is the output:
```

holli@holli-laptop:~$ sudo dhclient eth0
There is already a pid file /var/run/dhclient.pid with pid 9374
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:12:3f:dc:16:0c
Sending on   LPF/eth0/00:12:3f:dc:16:0c
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

```

holli@holli-laptop:~$ sudo dhclient eth1
There is already a pid file /var/run/dhclient.pid with pid 9458
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:12:f0:ac:bf:0a
Sending on   LPF/eth1/00:12:f0:ac:bf:0a
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPOFFER of 192.168.0.106 from 192.168.0.1
DHCPREQUEST of 192.168.0.106 on eth1 to 255.255.255.255 port 67
DHCPACK of 192.168.0.106 from 192.168.0.1
bound to 192.168.0.106 -- renewal in 42325 seconds.

```

---

### Post by superprash2003 on 2009-04-03
your eth1 seems to have got an ip 192.168.0.106 .. are things working now?

---

### Post by chicory on 2009-04-03
> **superprash2003 said:**
> your eth1 seems to have got an ip 192.168.0.106 .. are things working now?

Thank you for getting back to me.

No - I am afraid I still don't have the wired connection. I think eth1 is the wireless that I am forced to steal from my neighbor. The problem I'm having is with the wired connection, which, I believe, is eth0.

My wired router is 192.168.1.254, and the last IP I got assigned back when the connection was working was 192.168.1.111

---

### Post by superprash2003 on 2009-04-04
oh so things work fine via wireless?? check your wired router's DHCP settings to see if it is enabled

---

### Post by chicory on 2009-04-04
> **superprash2003 said:**
> oh so things work fine via wireless?? check your wired router's DHCP settings to see if it is enabled

I am pretty sure that DHCP settings on the router are enabled, since 3 other computers are plugged into it and all have internet without any problems. In fact if I simply take the cable from the problematic laptop connection and simply plug it into any a network card of any other computer - the connection gets established right away without any problems... So it looks like the problem is with the laptop, not with the router.

---

### Post by superprash2003 on 2009-04-05
try disabling ipv6  [http://www.prash-babu.com/2009/01/how-to-disable-ipv6-in-linux-ubuntu-to.html](http://www.prash-babu.com/2009/01/how-to-disable-ipv6-in-linux-ubuntu-to.html)

---

### Post by chicory on 2009-04-11
> **superprash2003 said:**
> try disabling ipv6  [http://www.prash-babu.com/2009/01/how-to-disable-ipv6-in-linux-ubuntu-to.html](http://www.prash-babu.com/2009/01/how-to-disable-ipv6-in-linux-ubuntu-to.html)

I'm sorry it took me awhile to get back to this - I got really busy at work, and had to put the laptop troubleshooting on hold.

I have disabled ipv6, but that did not help.

However, there are some changes in the situation. As I was trying to figure out what's wrong with the laptop, I have remembered that in addition to the Belkin-5020 card, I have another Ethernet port on this computer - the broken one that I was told not to use by the laptop's previous owner (which explains why Belkin PCMCIA card was needed to begin with.) When I tried to plug the network cable into the broken port the eth0 was immediately displayed as connected, but not a single page loaded, which confirmed the broken status of this port. 

So I went ahead and disabled this card in BIOS, since I presumed that its presence might interfere with the performance of Belkin PCMCIA. And now I do not have eth0 option at all, which leads me to presume that ether Linux does not recognize my PCMCIA card or sees it but fails to communicate with it or smth else. If I remove it from the slot and then put it back however, the $dmesg last two lines are:

```

[ 1988.472219] pccard: PCMCIA card inserted into slot 0
[ 1988.473298] cs: warning: no high memory space available!

```

So does it mean the system sees it? And if yes then where is it under $lspci, cause I don't see it: 

```

holli@holli-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc M22 [Mobility Radeon X300]
03:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
03:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08)
03:01.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)
03:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)

```

Any ideas would be helpful. I can enable the broken PCMCIA port anytime if you think disabling it is not helpful.

UPDATED ifconfig:
```

holli@holli-laptop:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:12:f0:ac:bf:0a  
          inet addr:192.168.0.102  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:26 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5333780 (5.3 MB)  TX bytes:307816 (307.8 KB)
          Interrupt:17 Memory:dfcff000-dfcfffff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:39 errors:0 dropped:0 overruns:0 frame:0
          TX packets:39 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3373 (3.3 KB)  TX bytes:3373 (3.3 KB)

```


UPDATED dhclient eth0 AND eth1:

```

holli@holli-laptop:~$ sudo dhclient eth0
[sudo] password for holli: 
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device


holli@holli-laptop:~$ sudo dhclient eth1
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:12:f0:ac:bf:0a
Sending on   LPF/eth1/00:12:f0:ac:bf:0a
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPOFFER of 192.168.0.102 from 192.168.0.1
DHCPREQUEST of 192.168.0.102 on eth1 to 255.255.255.255 port 67
DHCPACK of 192.168.0.102 from 192.168.0.1
bound to 192.168.0.102 -- renewal in 37195 seconds.

```

Please note that as far as I understand eth1 is my perfectly working wireless connection which I am forced to steal from my neighbor, while I am trying to fix my very own wired one.

---

### Post by chicory on 2009-04-14
Bump... The situation is still the same... 
Basically it comes down to a simple question - how can I tell if my PSMCIA card is working properly and is recognized by the system?

---

