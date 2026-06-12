---
title: "Trouble with Ubuntu and Internet"
date: 2011-07-12
forum: Networking &amp; Wireless
---

### Post by john_s2 on 2011-07-12
I have 3 laptops with 3 different OS - XP PRO, Win7 and Ubuntu (Linux). 
I try to connect to Internet in different locations using 2 different  Internet Service Providers (ISP) and straight cable connection (not  wireless).

Scenario 1: ISP number 1 - all 3 laptops can access Internet
Scenario 2: ISP number 2 - only Microsoft OS based laptops can access Internet

I wonder if anybody knows what might be the problem?

Thanks,

---

### Post by doas777 on 2011-07-12
are you plugging the laptop directly into the cablemodem, or is there a router or other piece of equipment inline? most cablemodems don;t like having their devices switched about without a powercycle. try plugging in the ubuntu laptop, and unplug the modem from the wall for a minute or two. 

ISP2 isn't [BT with a HomeHub]("http://community.bt.com/t5/BB-Speed-Connection-Issues/BT-HomeHub-firmware-upgrade-broken-network-connectivity-Ubuntu/td-p/176473/page/9"), is it?

---

### Post by john_s2 on 2011-07-12
Scenario 1: each laptop via cat5 cable directly into Motorola cable modem (one at a time of course :-) and this config works as a charm with all three PCs

Scenario 2: that route is more tricky as it is a rural ISP. and quite convoluted way to get through; from ISP via wireless link to AP1, that has a router serving that single AP1 location PCs, then a bridge between AP1 and AP2 and finally the Powered over Internet end-device that has a CAT5 cable available to connect each of my trial laptops one at a time. And here's the catch - MS laptops obtain IP just fine while Ubuntu does NOT.

---

### Post by doas777 on 2011-07-12
well, then, lets determine teh scope of the issue.

from an affected ubuntu machine, run
```

sudo ifconfig -a
nslookup ubuntuforums.org
route

```and from an unaffected windows machine, run
```

ipconfig /all
nslookup ubuntuforums.org
route print

```and post back the results.

---

### Post by john_s2 on 2011-07-12
Thanks a lot!

Will do it tomorrow as the rural site is an hour drive from here :-)

---

### Post by doas777 on 2011-07-12
kewl. 

in that case, I'll give you a few other commands. no idea if they will be useful yet, but if its a hike, better to test everything all at once:

on the ubuntu box, run
```

sudo cat /etc/network/interfaces
sudo cat /etc/resolv.conf
sudo ifconfig -a
sudo ufw status

```

if the problem appears to be related to the ip address, and you are using DHCP, run this command, and see if you get a valid address:
```

sudo dhclient

```

if the windows system and the ubuntu system are using differant DNS servers, but have valid IP addresses, try editing /etc/resolv.conf and adding a line like:
```
nameserver <IP address of windows dns server>
```, save the file, and restart networking with:
```
sudo /etc/init.d/networking restart
```
and try the nslookup again. if it resolves, you are golden.

---

### Post by john_s2 on 2011-07-12
Thanks, I'll post the results tomorrow (hopefully from that remote site).

---

### Post by john_s2 on 2011-07-13
> **john_s2 said:**
> ... Powered over Internet end-device ...

I was dreaming ... PoE of course :D

---

### Post by john_s2 on 2011-07-13
Reply to 
ipconfig /all
etc...
from XP PRO laptop (went online with no problems)

[PHP]Microsoft Windows XP [Version 5.1.2600]
(C) Copyright 1985-2001 Microsoft Corp.

C:\Documents and Settings\Jan>ipconfig /all

Windows IP Configuration

        Host Name . . . . . . . . . . . . : JOBBER
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Broadcast
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : Broadcom NetXtreme 57xx Gigabit Cont
roller
        Physical Address. . . . . . . . . : 00-14-22-F6-80-5C
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 192.168.1.187
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.1.1
        DHCP Server . . . . . . . . . . . : 192.168.1.1
        DNS Servers . . . . . . . . . . . : 142.166.86.18
                                            142.166.86.19
                                            192.168.1.1
        Lease Obtained. . . . . . . . . . : Wednesday, July 13, 2011 2:09:19 PM
        Lease Expires . . . . . . . . . . : Thursday, July 14, 2011 2:09:19 PM

Ethernet adapter Wireless Network Connection:

        Media State . . . . . . . . . . . : Media disconnected
        Description . . . . . . . . . . . : Dell Wireless 1390 WLAN Mini-Card
        Physical Address. . . . . . . . . : 00-16-CE-50-3D-DA

C:\Documents and Settings\Jan>nslookup ubuntuforums.org
Server:  ns1.xplornet.com
Address:  142.166.86.18

Non-authoritative answer:
Name:    ubuntuforums.org
Address:  91.189.94.12


C:\Documents and Settings\Jan>route print
===========================================================================
Interface List
0x1 ........................... MS TCP Loopback interface
0x2 ...00 14 22 f6 80 5c ...... Broadcom NetXtreme 57xx Gigabit Controller - Pac
ket Scheduler Miniport
0x3 ...00 16 ce 50 3d da ...... Dell Wireless 1390 WLAN Mini-Card - Packet Sched
uler Miniport
===========================================================================
===========================================================================
Active Routes:
Network Destination        Netmask          Gateway       Interface  Metric
          0.0.0.0          0.0.0.0      192.168.1.1   192.168.1.187       20
        127.0.0.0        255.0.0.0        127.0.0.1       127.0.0.1       1
      192.168.1.0    255.255.255.0    192.168.1.187   192.168.1.187       20
    192.168.1.187  255.255.255.255        127.0.0.1       127.0.0.1       20
    192.168.1.255  255.255.255.255    192.168.1.187   192.168.1.187       20
        224.0.0.0        240.0.0.0    192.168.1.187   192.168.1.187       20
  255.255.255.255  255.255.255.255    192.168.1.187   192.168.1.187       1
  255.255.255.255  255.255.255.255    192.168.1.187               3       1
Default Gateway:       192.168.1.1
===========================================================================
Persistent Routes:
  None

C:\Documents and Settings\Jan>[/PHP]

---

### Post by john_s2 on 2011-07-13
This one is from my Ubuntu laptop that cannot connect to Internet...
Mind you I'm a total Linux newbie and it took me 1/2 hour to figure out how to capture that terminal text as a my.txt file ... I couldn't find a "plain" "Save as TXT" comand inside terminal... any hints?

[PHP]eth0      Link encap:Ethernet  HWaddr bc:ae:c5:58:b7:76  
          inet6 addr: fe80::beae:c5ff:fe58:b776/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:843 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26 errors:0 dropped:0 overruns:0 carrier:4
          collisions:0 txqueuelen:1000 
          RX bytes:80327 (80.3 KB)  TX bytes:3676 (3.6 KB)
          Interrupt:29 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:58 errors:0 dropped:0 overruns:0 frame:0
          TX packets:58 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5996 (5.9 KB)  TX bytes:5996 (5.9 KB)

wlan0     Link encap:Ethernet  HWaddr 48:5d:60:de:ea:e0  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 48-5D-60-DE-EA-E0-00-00-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
[/PHP]

---

### Post by doas777 on 2011-07-13
> **john_s2 said:**
> This one is from my Ubuntu laptop that cannot connect to Internet...
Mind you I'm a total Linux newbie and it took me 1/2 hour to figure out how to capture that terminal text as a my.txt file ... I couldn't find a "plain" "Save as TXT" comand inside terminal... any hints?

[PHP]eth0      Link encap:Ethernet  HWaddr bc:ae:c5:58:b7:76  
          inet6 addr: fe80::beae:c5ff:fe58:b776/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:843 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26 errors:0 dropped:0 overruns:0 carrier:4
          collisions:0 txqueuelen:1000 
          RX bytes:80327 (80.3 KB)  TX bytes:3676 (3.6 KB)
          Interrupt:29 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:58 errors:0 dropped:0 overruns:0 frame:0
          TX packets:58 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5996 (5.9 KB)  TX bytes:5996 (5.9 KB)

wlan0     Link encap:Ethernet  HWaddr 48:5d:60:de:ea:e0  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 48-5D-60-DE-EA-E0-00-00-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
[/PHP]
Tonight is role-playing game night, so I'll have to check your output later tonight, but when I want to extract data from the terminal, I usually highlight with a mouse, and use  ctrl + Shift + C to copy, or rightclick on the highlighted text and select copy.

just from a glance, your ubuntu does not have an ip address, whereas the windows ip is [COLOR=#000000][COLOR=#007700][/COLOR][COLOR=#0000BB]192.168.1.187.

run [/COLOR][/COLOR]```
[COLOR=#000000][COLOR=#0000BB][/COLOR][/COLOR]sudo dhclient
``` and postback the output.[COLOR=#000000][COLOR=#0000BB][/COLOR][/COLOR]

---

### Post by john_s2 on 2011-07-13
sudo dhclient

[PHP]user@ekoview:~$ sudo dhclient
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/48:5d:60:de:ea:e0
Sending on   LPF/wlan0/48:5d:60:de:ea:e0
Listening on LPF/eth0/bc:ae:c5:58:b7:76
Sending on   LPF/eth0/bc:ae:c5:58:b7:76
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9[/PHP]

---

### Post by john_s2 on 2011-07-14
Well, here's another quick report I tested just hours ago from another local location using ADSL ISP, and as you can see obtaining IP just fine with Ubuntu laptop.  Same config and direct cable connected to ADSL modem this time as it's Telus in Calgary. 

And again -  it's the same Ubuntu only laptop and without any setup changes. As you can see it works just fine and obtains IP address via DHCP... 

The below code is just to prove that Ubuntu DHCP worked fine in another non-rural location.

```
user@ekoview:~$ sudo dhclient
[sudo] password for user: 
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/48:5d:60:de:ea:e0
Sending on   LPF/wlan0/48:5d:60:de:ea:e0
Listening on LPF/eth0/bc:ae:c5:58:b7:76
Sending on   LPF/eth0/bc:ae:c5:58:b7:76
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPOFFER of 192.168.1.68 from 192.168.1.254
DHCPREQUEST of 192.168.1.68 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.68 from 192.168.1.254
 * Reloading /etc/samba/smb.conf smbd only
   ...done.
bound to 192.168.1.68 -- renewal in 39732 seconds.
user@ekoview:~$ sudo ifconfig -a
eth0      Link encap:Ethernet  HWaddr bc:ae:c5:58:b7:76  
          inet addr:192.168.1.68  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::beae:c5ff:fe58:b776/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:204 errors:0 dropped:0 overruns:0 frame:0
          TX packets:294 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:158098 (158.0 KB)  TX bytes:40461 (40.4 KB)
          Interrupt:29 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

wlan0     Link encap:Ethernet  HWaddr 48:5d:60:de:ea:e0  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 48-5D-60-DE-EA-E0-00-00-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

user@ekoview:~$ sudo cat /etc/network/interfaces
auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth0
user@ekoview:~$ sudo cat /etc/resolv.conf
domain home
search home
nameserver 192.168.1.254
user@ekoview:~$ sudo ifconfig -a
eth0      Link encap:Ethernet  HWaddr bc:ae:c5:58:b7:76  
          inet addr:192.168.1.68  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::beae:c5ff:fe58:b776/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:224 errors:0 dropped:0 overruns:0 frame:0
          TX packets:313 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:159686 (159.6 KB)  TX bytes:42495 (42.4 KB)
          Interrupt:29 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:34 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3812 (3.8 KB)  TX bytes:3812 (3.8 KB)

wlan0     Link encap:Ethernet  HWaddr 48:5d:60:de:ea:e0  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0:avahi Link encap:Ethernet  HWaddr 48:5d:60:de:ea:e0  
          inet addr:169.254.12.192  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

wmaster0  Link encap:UNSPEC  HWaddr 48-5D-60-DE-EA-E0-00-00-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

user@ekoview:~$ sudo dhclient
There is already a pid file /var/run/dhclient.pid with pid 1999
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/48:5d:60:de:ea:e0
Sending on   LPF/wlan0/48:5d:60:de:ea:e0
Listening on LPF/eth0/bc:ae:c5:58:b7:76
Sending on   LPF/eth0/bc:ae:c5:58:b7:76
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPREQUEST of 192.168.1.68 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.68 from 192.168.1.254
 * Reloading /etc/samba/smb.conf smbd only
   ...done.
bound to 192.168.1.68 -- renewal in 36949 seconds.
user@ekoview:~$ sudo ufw status
Status: inactive
user@ekoview:~$ 



```One more thing - originally I requested a static IP addr to be assigned  to the remote location so that I could access that remote AP from my  office.  And I believe the rural ISP provided it. 

But even then and despite all of that a DHCP (and NOT hard coded  addressing) still works just fine with XP and Win7 laptops while failing  with Ubuntu.

What's so different with Ubuntu failing DHCP in remote Site, and how to figure out what stops it just in that single location?

---

### Post by doas777 on 2011-07-14
try disabling ipv6 on the laptop, and try again.
[http://www.ubuntugeek.com/how-to-disable-ipv6-in-ubuntu.html](http://www.ubuntugeek.com/how-to-disable-ipv6-in-ubuntu.html)

I've seen several references to it interfering with some dhcp server configurations. BTW, i think the real source of the issue is with the dhcp server rather than your boxen, but thats just a hunch for now.

---

### Post by john_s2 on 2011-07-14
OK, I'll disable ipv6 tomorrow.

Also, the difference is that rural locations uses a wireless ISP+router+bridged access point (AP). And as one fellow suggested...

"... sounds like that  router may be your problem. If it functions as a  gateway/firewall there are several ways it might block your laptop from  reaching the internet.  

Wifi adds another layer of complexity and I have recently noticed a  local wifi spot which includes a login for guests and a firewall will  time out Linux while operate well on W7.  Hopefully, MS hasn't found a  way to hog wifi use. That problem seems to be involving the browsers IE8  versus Firefox...."

And I use Firefox in all 3 laptops.

---

### Post by john_s2 on 2011-07-15
> **doas777 said:**
> try disabling ipv6 on the laptop, and try again.
[http://www.ubuntugeek.com/how-to-disable-ipv6-in-ubuntu.html](http://www.ubuntugeek.com/how-to-disable-ipv6-in-ubuntu.html)

I've seen several references to it interfering with some dhcp server configurations. BTW, i think the real source of the issue is with the dhcp server rather than your boxen, but thats just a hunch for now.

I could not edit aliases (Method 1) as the /etc/modprobes/aliase was empty.
I used the other 2 methods and disabled IPv6 in Firefox (Method 2) and in /etc/default/grub file (Method 3). Saved, restarted and... still no connection to Internet. 

Am going to connect directly to the very 1st router to see if it gets IP from there...

(updated minutes later) Yeah, it works from entry router just fine. Soooo it's the wireless enGenius bridge that seems to cause the problem - but why just Ubuntu???

---

### Post by john_s2 on 2011-07-18
> **doas777 said:**
> try disabling ipv6 on the laptop, and try again.
[http://www.ubuntugeek.com/how-to-disable-ipv6-in-ubuntu.html](http://www.ubuntugeek.com/how-to-disable-ipv6-in-ubuntu.html)

I've seen several references to it interfering with some dhcp server configurations. BTW, i think the real source of the issue is with the dhcp server rather than your boxen, but thats just a hunch for now.

Do you have any additional thoughts on how to resolve it as I run out of ideas? 

I appreciate any feedback from you...

---

### Post by jmoorse on 2011-07-18
John, we can take a look at the network traffic and see if the issue surfaces.  As I understand it you are connecting via eth0 (ethernet cable)

Please open 2 terminal windows, in one run:

```

sudo tcpdump -i eth0 udp port 67 or udp port 68 -vvvv -s0 -n

```

Once that is running, in the second terminal run:

```

sudo dhclient

```

Please provide the output from both commands, thanks!

---

### Post by john_s2 on 2011-07-18
> **jmoorse said:**
> John, we can take a look at the network traffic and see if the issue surfaces.  As I understand it you are connecting via eth0 (ethernet cable)

Please open 2 terminal windows, in one run:

```

sudo tcpdump -i eth0 udp port 67 or udp port 68 -vvvv -s0 -n

```Once that is running, in the second terminal run:

```

sudo dhclient

```Please provide the output from both commands, thanks!

It's always and only via Ethernet cable.

Question: should I try y/code at the remote "dead" AP or at the "local" router point?

---

### Post by jmoorse on 2011-07-18
Let's try at the location that is having problems.  

This is going to test if you are even getting DHCP responses there which are not being processed for some reason.

---

### Post by john_s2 on 2011-07-18
OK, will try in 2 days as I plan to travel there again...

---

### Post by doas777 on 2011-07-19
> **john_s2 said:**
> Do you have any additional thoughts on how to resolve it as I run out of ideas? 

I appreciate any feedback from you...
well, my thought is that we have narrowed it down to DHCP. I have little experience with advanced dhcp, so hopefully someone more experienced will drop in. I've just never had any problems with it.

about the only think I can suggest is to check to make sure you aren't firewalling udp\68 inbound. 

you can check your firewall status with 
```
sudo ufw status
```

---

### Post by john_s2 on 2011-07-20
sudo ufw status

Status: inactive

---

### Post by john_s2 on 2011-07-20
> **jmoorse said:**
> John, we can take a look at the network traffic and see if the issue surfaces.  As I understand it you are connecting via eth0 (ethernet cable)

Please open 2 terminal windows, in one run:

```

sudo tcpdump -i eth0 udp port 67 or udp port 68 -vvvv -s0 -n

```Once that is running, in the second terminal run:

```

sudo dhclient

```Please provide the output from both commands, thanks!


 1st one cannot even go through as it says "WARNING: eth0: no IPv4 address assigned"

... but that we knew already...

tons of stuff after approx 1min - will report later

---

### Post by john_s2 on 2011-07-21
My final answer is .... it's engenius bridge and ubuntu not willing to cooperate. 

Problem's not solved and I decided to pull the plug and order a separate internet line directly to that remote AP.

---

