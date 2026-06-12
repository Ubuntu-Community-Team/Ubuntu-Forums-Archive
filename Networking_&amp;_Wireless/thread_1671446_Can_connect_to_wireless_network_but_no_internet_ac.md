---
title: "Can connect to wireless network but no internet access"
date: 2011-01-20
forum: Networking &amp; Wireless
---

### Post by DHart07 on 2011-01-20
I have had a heck of a time trying to get my laptop running ubuntu to connect to my home network.  I have managed to get it to work at my university which would seemingly be more difficult than getting it to work at home, so I know for a fact it isn't a hardware or driver issue.

If I try to connect via ethernet cable from my router, it detects that I connected the cable but says "disconnected" and never lets me connect.  If I SKIP the router and go from my modem directly to my laptop via ethernet cable it works great.  

Using the wireless network tool I can see all of the wireless connections in my area.  When I go to connect to my network it prompts me for the WEP key and when I enter it and hit connect it just keeps cycling and eventually times out and finally again prompts me for my WEP key.  I know this network works as it works just fine on my Windows 7 partition.  Another interesting note - both my wireless and ethernet connections both worked flawlessly and stoopid easily on the live cd but don't after the full install.

If I manually enter in the information for my wireless through IPv4 settings and enter in the  Address,Netmask and gateway I can connect to my network - but then I have no active internet connection.  Same deal with my wired connection.  Is this because choosing this manual method grays out the DHCP?  What am I missing here?

---

### Post by amsterdamharu on 2011-01-20
Taken from the other thread that has died out a bit:

The problem can't be the router settings since it works on live CD, DHCP is enabled in the router but it seems no IP address is given or not accepted.
The network cards in use are:

```

01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
    Subsystem: Toshiba America Info Systems Device ff1e
    Kernel driver in use: r8169
    Kernel modules: r8169
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller (rev 10)
    Subsystem: Realtek Semiconductor Co., Ltd. Device 8181
    Kernel driver in use: rtl819xSE
    Kernel modules: r8192se_pci
```

Output when switching the cards on and off:
```
dave@dave-Satellite-A505 ~ $ sudo ifconfig eth0 down
dave@dave-Satellite-A505 ~ $ sudo ifconfig eth0 up
dave@dave-Satellite-A505 ~ $ tail tail /var/log/daemon.log
tail: cannot open `tail' for reading: No such file or directory
==> /var/log/daemon.log <==
Jan 16 21:39:02 dave-Satellite-A505 avahi-daemon[952]: Leaving mDNS multicast group on interface eth0.IPv6 with address fe80::226:6cff:fe41:a048.
Jan 16 21:39:02 dave-Satellite-A505 avahi-daemon[952]: Withdrawing address record for fe80::226:6cff:fe41:a048 on eth0.
Jan 16 21:39:02 dave-Satellite-A505 NetworkManager[1044]: <info> (eth0): carrier now OFF (device state 3)
Jan 16 21:39:02 dave-Satellite-A505 NetworkManager[1044]: <info> (eth0): device state change: 3 -> 2 (reason 40)
Jan 16 21:39:02 dave-Satellite-A505 NetworkManager[1044]: <info> (eth0): deactivating device (reason: 40).
Jan 16 21:39:07 dave-Satellite-A505 NetworkManager[1044]: <info> (eth0): carrier now ON (device state 2)
Jan 16 21:39:07 dave-Satellite-A505 NetworkManager[1044]: <info> (eth0): device state change: 2 -> 3 (reason 40)
Jan 16 21:39:08 dave-Satellite-A505 avahi-daemon[952]: Joining mDNS multicast group on interface eth0.IPv6 with address fe80::226:6cff:fe41:a048.
Jan 16 21:39:08 dave-Satellite-A505 avahi-daemon[952]: New relevant interface eth0.IPv6 for mDNS.
Jan 16 21:39:08 dave-Satellite-A505 avahi-daemon[952]: Registering new address record for fe80::226:6cff:fe41:a048 on eth0.*.
dave@dave-Satellite-A505 ~ $ tail /var/log/faillog
dave@dave-Satellite-A505 ~ $

```

And requesting a new IP address:
```
dave@dave-Satellite-A505 ~ $ sudo dhclient
There is already a pid file /var/run/dhclient.pid with pid 3420
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth0/00:26:6c:41:a0:48
Sending on   LPF/eth0/00:26:6c:41:a0:48
Listening on LPF/wlan0/70:1a:04:d3:e4:54
Sending on   LPF/wlan0/70:1a:04:d3:e4:54
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPOFFER of 192.168.2.136 from 192.168.2.1
DHCPREQUEST of 192.168.2.136 on eth0 to 255.255.255.255 port 67
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPNAK from 192.168.2.1
DHCPREQUEST of 192.168.2.136 on eth0 to 255.255.255.255 port 67
DHCPNAK from 192.168.2.1
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPOFFER of 192.168.2.136 from 192.168.2.1
DHCPREQUEST of 192.168.2.136 on eth0 to 255.255.255.255 port 67
DHCPNAK from 192.168.2.1
DHCPREQUEST of 192.168.2.136 on eth0 to 255.255.255.255 port 67
DHCPNAK from 192.168.2.1
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPOFFER of 192.168.2.137 from 192.168.2.1
DHCPREQUEST of 192.168.2.137 on eth0 to 255.255.255.255 port 67
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPNAK from 192.168.2.1
DHCPREQUEST of 192.168.2.137 on eth0 to 255.255.255.255 port 67
DHCPNAK from 192.168.2.1
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPOFFER of 192.168.2.137 from 192.168.2.1
DHCPREQUEST of 192.168.2.137 on eth0 to 255.255.255.255 port 67
DHCPNAK from 192.168.2.1
DHCPREQUEST of 192.168.2.137 on eth0 to 255.255.255.255 port 67
DHCPNAK from 192.168.2.1
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPREQUEST of 192.168.2.137 on eth0 to 255.255.255.255 port 67
DHCPNAK from 192.168.2.1
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 2
DHCPOFFER of 192.168.2.136 from 192.168.2.1
DHCPREQUEST of 192.168.2.136 on eth0 to 255.255.255.255 port 67
DHCPNAK from 192.168.2.1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

Looks like DHCPACK is missing so although a DHCP address is asked for and offered it is never accepted.

I am stuck and can't think of anything that could help out anymore.

---

### Post by slooksterpsv on 2011-01-20
> **DHart07 said:**
> ...

If I try to connect via ethernet cable from my router, it detects that I connected the cable but says "disconnected" and never lets me connect.  If I SKIP the router and go from my modem directly to my laptop via ethernet cable it works great.  



Powercycle all of your equipment, e.g. unplug router and modem, let set for 30 seconds, then plug it in

> 

Using the wireless network tool I can see all of the wireless connections in my area.  When I go to connect to my network it prompts me for the WEP key and when I enter it and hit connect it just keeps cycling and eventually times out and finally again prompts me for my WEP key.


Make sure that you're entering the right key, even click on show key and verify. :-s

> 
...

If I manually enter in the information for my wireless through IPv4 settings and enter in the  Address,Netmask and gateway I can connect to my network - but then I have no active internet connection.  Same deal with my wired connection.  Is this because choosing this manual method grays out the DHCP?  What am I missing here?

Not necessarily, even though it thinks your connecting you may not be. If you can't fully authenticate against your router, its just not going to work, even with putting in static information (manually specifying IP, etc.) cause of it needing to negotiate that it has the right key.

Have you tried additional ports on the back of the router, making sure that the port isn't going bad (they do go bad)? (Just to test Ethernet)

Overall, verify the key, make sure you enter the letters and numbers, correctly - not case sensitive, try some of those and let us know ok.
:D:D

---

### Post by DHart07 on 2011-01-20
I am 100% sure the key is right as I made it stupid simple and simply set it to all a's.  The ethernet port is good because I unplug the ethernet cable from my desktop to plug it into my laptop and the desktop is always fine.  I understand that if I can never authenticate the router that it wont work, but then why does it work on the live cd?

---

### Post by amsterdamharu on 2011-01-20
[http://www.tcpipguide.com/free/t_DHCPGeneralOperationandClientFiniteStateMachine.htm](http://www.tcpipguide.com/free/t_DHCPGeneralOperationandClientFiniteStateMachine.htm)
Instead of a [FONT=Arial]** *DHCPACK***[/FONT]you get [FONT=Arial][B] [I]DHCPNACK 
[/I][/B][/FONT]"t[FONT=Arial]he client receives a *DHCPNAK* message from its chosen server,  which means the server has withdrawn its offer. The client returns to  the *INIT* state.[/FONT]"

The only thing we haven't tried yet is disable ipv6 maybe that might help a bit:

Press alt + F2, type "gksudo gedit  /etc/modprobe.d/aliases" (no quotes) and click run
change
```
alias net-pf-10 ipv6
```
to
```
alias net-pf-10 off
```
Restart
If that didn't work then change
```
alias net-pf-10 off
```
to
```
alias net-pf-10 off ipv6
```
Restart
From the following website:
[http://www.ubuntugeek.com/how-to-disable-ipv6-in-ubuntu.html](http://www.ubuntugeek.com/how-to-disable-ipv6-in-ubuntu.html)

---

### Post by richard.peter3 on 2011-05-09
I had the same problem. I am new to ubuntu so take it easy. 

I am connecting with an Ethernet cable, eth0, I have tried the above solution to change the modprobe.d/aliases file I've restarted and turned my bt homehub off several times/changed the socket. 

When I run
Sudo dhclient eth0 
I get
Dhcpdiscover on eth0 255.255.255.255 port 67 interval 3
Du porter of 192.168.1.83
Dhcprequest of 192.168.1.83 on eth0 to 255.255.255.255 port 67
Dhcpnak from 192.168.1.254
Dhcprequest...
Dhcpnak...
Etc...

Was this issue ever resolved?

Fyi : I think I updated my ubuntu software around the time it stopped working
My installs on the 8th were 
Samba
Perl
Ubuntuone-client-gnome 
Vino
Other clagg that looks innocuous

Ubuntu version 10.10
gnome 2.32.0

Hope this helps.

---

