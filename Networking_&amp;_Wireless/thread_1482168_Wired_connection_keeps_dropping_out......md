---
title: "Wired connection keeps dropping out....."
date: 2010-05-13
forum: Networking &amp; Wireless
---

### Post by MuseFan on 2010-05-13
Hello!

Two weeks ago I decided to ditch my XP install completely and switch to Ubuntu 10.04. So far so good, and I'm very happy with my decision. However, about 3 days ago, my wired connection started playing up. It keeps dropping out every 2 hours or so between 13.00 and 04.00. After dropping out, it immediately reconnects again (at least when I use Automatically DCHP config). From 04.00 to 13.00 it is more or less stable. 

I tried resolving by reserving an IP in the DCHP Client Table in my router (linksys WRT120N). Additionally, I told the Network Manager to use the Manual configuration. Unfortunately these changes didn't help and the problems stay the same......

The **daemon.log** shows the following information:

```
May 13 04:09:55 musefan-desktop NetworkManager: <info>  (eth0): carrier now OFF (device state 8, deferring action for 4 seconds)
May 13 04:10:00 musefan-desktop NetworkManager: <info>  (eth0): device state change: 8 -> 2 (reason 40)
May 13 04:10:00 musefan-desktop NetworkManager: <info>  (eth0): deactivating device (reason: 40).
May 13 04:10:00 musefan-desktop NetworkManager: <info>  (eth0): canceled DHCP transaction, dhcp client pid 22635
May 13 04:10:00 musefan-desktop NetworkManager: <WARN>  check_one_route(): (eth0) error -34 returned from rtnl_route_del(): Sucess#012
May 13 04:10:00 musefan-desktop avahi-daemon[857]: Withdrawing address record for 192.168.1.101 on eth0.
May 13 04:10:00 musefan-desktop avahi-daemon[857]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.1.101.
May 13 04:10:00 musefan-desktop avahi-daemon[857]: Interface eth0.IPv4 no longer relevant for mDNS.
May 13 04:10:04 musefan-desktop NetworkManager: <info>  (eth0): carrier now ON (device state 2)
May 13 04:10:04 musefan-desktop NetworkManager: <info>  (eth0): device state change: 2 -> 3 (reason 40)
May 13 04:10:04 musefan-desktop NetworkManager: <info>  Activation (eth0) starting connection 'Auto eth0'
May 13 04:10:04 musefan-desktop NetworkManager: <info>  (eth0): device state change: 3 -> 4 (reason 0)
May 13 04:10:04 musefan-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
May 13 04:10:04 musefan-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started...
May 13 04:10:04 musefan-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
May 13 04:10:04 musefan-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
May 13 04:10:04 musefan-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting...
May 13 04:10:04 musefan-desktop NetworkManager: <info>  (eth0): device state change: 4 -> 5 (reason 0)
May 13 04:10:04 musefan-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful.
May 13 04:10:04 musefan-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
May 13 04:10:04 musefan-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete.
May 13 04:10:04 musefan-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
May 13 04:10:04 musefan-desktop NetworkManager: <info>  (eth0): device state change: 5 -> 7 (reason 0)
May 13 04:10:04 musefan-desktop NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction (timeout in 45 seconds)
May 13 04:10:04 musefan-desktop NetworkManager: <info>  dhclient started with pid 22757
May 13 04:10:04 musefan-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) scheduled...
May 13 04:10:04 musefan-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
May 13 04:10:04 musefan-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) started...
May 13 04:10:04 musefan-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) complete.
May 13 04:10:04 musefan-desktop dhclient: Internet Systems Consortium DHCP Client V3.1.3
May 13 04:10:04 musefan-desktop dhclient: Copyright 2004-2009 Internet Systems Consortium.
May 13 04:10:04 musefan-desktop dhclient: All rights reserved.
May 13 04:10:04 musefan-desktop dhclient: For info, please visit https://www.isc.org/software/dhcp/
May 13 04:10:04 musefan-desktop dhclient: 
May 13 04:10:04 musefan-desktop NetworkManager: <info>  DHCP: device eth0 state changed normal exit -> preinit
May 13 04:10:04 musefan-desktop dhclient: Listening on LPF/eth0/**mac-address**
May 13 04:10:04 musefan-desktop dhclient: Sending on   LPF/eth0/**mac-address**
May 13 04:10:04 musefan-desktop dhclient: Sending on   Socket/fallback
May 13 04:10:05 musefan-desktop dhclient: DHCPREQUEST of 192.168.1.101 on eth0 to 255.255.255.255 port 67
May 13 04:10:06 musefan-desktop NetworkManager: <info>  (eth0): carrier now OFF (device state 7, deferring action for 4 seconds)
May 13 04:10:08 musefan-desktop dhclient: DHCPREQUEST of 192.168.1.101 on eth0 to 255.255.255.255 port 67
May 13 04:10:08 musefan-desktop NetworkManager: <info>  (eth0): carrier now ON (device state 7)
May 13 04:10:12 musefan-desktop dhclient: DHCPREQUEST of 192.168.1.101 on eth0 to 255.255.255.255 port 67
May 13 04:10:16 musefan-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
May 13 04:10:16 musefan-desktop dhclient: DHCPOFFER of 192.168.1.101 from 192.168.1.1
May 13 04:10:16 musefan-desktop dhclient: DHCPREQUEST of 192.168.1.101 on eth0 to 255.255.255.255 port 67
May 13 04:10:16 musefan-desktop dhclient: DHCPACK of 192.168.1.101 from 192.168.1.1
May 13 04:10:16 musefan-desktop dhclient: bound to 192.168.1.101 -- renewal in 39108 seconds.
May 13 04:10:16 musefan-desktop NetworkManager: <info>  DHCP: device eth0 state changed preinit -> bound
May 13 04:10:16 musefan-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) scheduled...
May 13 04:10:16 musefan-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) started...
May 13 04:10:16 musefan-desktop NetworkManager: <info>    address 192.168.1.101
May 13 04:10:16 musefan-desktop NetworkManager: <info>    prefix 24 (255.255.255.0)
May 13 04:10:16 musefan-desktop NetworkManager: <info>    gateway 192.168.1.1
May 13 04:10:16 musefan-desktop NetworkManager: <info>    nameserver '**removed nameserver**'
May 13 04:10:16 musefan-desktop NetworkManager: <info>    nameserver '**removed nameserver**'
May 13 04:10:16 musefan-desktop NetworkManager: <info>    domain name '**removed the domain name**'
May 13 04:10:16 musefan-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
May 13 04:10:16 musefan-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) complete.
May 13 04:10:16 musefan-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
May 13 04:10:16 musefan-desktop avahi-daemon[857]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.101.
May 13 04:10:16 musefan-desktop avahi-daemon[857]: New relevant interface eth0.IPv4 for mDNS.
May 13 04:10:16 musefan-desktop avahi-daemon[857]: Registering new address record for 192.168.1.101 on eth0.IPv4.
May 13 04:10:17 musefan-desktop NetworkManager: <info>  (eth0): device state change: 7 -> 8 (reason 0)
May 13 04:10:17 musefan-desktop NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.
May 13 04:10:17 musefan-desktop NetworkManager: <info>  Activation (eth0) successful, device activated.
May 13 04:10:17 musefan-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
May 13 04:10:31 musefan-desktop ntpdate[22814]: adjust time server 91.189.94.4 offset -0.236109 sec
```

**ifconfig**
```
eth0      Link encap:Ethernet  HWaddr **removed mac address**  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:92ff:fe3b:b8d6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:118785498 errors:0 dropped:0 overruns:0 frame:0
          TX packets:133541634 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:930726009 (930.7 MB)  TX bytes:1139183275 (1.1 GB)
          Interrupt:26 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:575882 errors:0 dropped:0 overruns:0 frame:0
          TX packets:575882 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:116587650 (116.5 MB)  TX bytes:116587650 (116.5 MB)

```

**lspci -nn**
```
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 01)
```

I hope someone able to help me get rid of this annoying problem..... Thank you in advance!

---

### Post by MuseFan on 2010-05-14
I think I found a possible cause for my problem.....since last night I decided turn off aMule to see what would happen, and I've got a stable connection for more than 24 hours now :)
So, I guess it can have something to do with the maximum number of connections aMule is making simultaneously. I will test some settings and see what's appropiate. Somehow, I didn't expect this to affect the Network Manager....

---

### Post by MuseFan on 2010-05-15
Hmmm.....it seems like the Network Manager is allergic of aMule at all :S I've put the maximum numbr of connections from 400 to 100. And the max number of connection per 5 seconds from 20 to 10. The problem still persists, although as far as I can tell now only once in 12 hours.....

Are problems known with the Network Manager and large numbers of connections?

---

### Post by MuseFan on 2010-05-16
Problem still persists....just de-installed Network Manager and added the eth0 connection to the /etc/network/interfaces file (and restarted network).

Let's see if that helps......

---

### Post by MuseFan on 2010-05-17
Well, it's solved. My router can't handle lots of connections.

Bit strange though that I never had these problems in Windows XP SP2. Does Linux deal differently with connection limits in comparison to Windows?

---

### Post by herrmoody on 2010-05-19
Having a similar problem and looking for someone with a solution I found your posts.  I think this is not a Linux problem per se, but something unique to 10.04.  I've used the prior versions of Ubuntu with no problems.  But something in this version doesn't like my network card or something about my network configuration and it's constantly shutting itself off and turning itself back on again.  It's certainly possible the network manager is at fault in this.  I'm not seeing anything in any logs that provides particularly helpful information for troubleshooting.

---

### Post by herrmoody on 2010-05-19
Scratch the theory on Network Manager on my iteration of this problem (which may be different than yours).  I just removed NM and replaced it with a completely manual network configuration and still have the problem.

---

### Post by sf_basilix on 2010-07-07
I am also having a problem with Ubuntu 10.04 on a Dell Latitude e6510 laptop.  The only application that I really have running is Virtualbox (running a windows xp guest os) and a browser in Ubuntu.  Every so often, the browser stops working in Ubuntu and I have to resort running this command to get networking back:

# sudo dhclient eth0

My networking returns and this will work for a few hours until it happens again.

---

### Post by herrmoody on 2010-07-07
In my case I actually eventually determined that the problem had nothing (or pretty much nothing) to do with Ubuntu.  The miniswitch that my computer was plugged into had some kind of flakey problem.  After moving my computer off of the miniswitch and plugging it directly into the router I've had no problems.  It may be that the current version of Ubuntu was more sensitive to the problem with the switch and reacted in a different way than the other OS's I've used the switch on, but I'm sure the switch itself was the core of the problem.

---

### Post by chandra on 2010-07-07
> **herrmoody said:**
> Scratch the theory on Network Manager on my iteration of this problem (which may be different than yours).  I just removed NM and replaced it with a completely manual network configuration and still have the problem.

Have you tried replacing NM with wicd?
```
sudo apt-get install wicd
```

It might help.

---

### Post by sf_basilix on 2010-09-02
> **herrmoody said:**
> In my case I actually eventually determined that the problem had nothing (or pretty much nothing) to do with Ubuntu.  The miniswitch that my computer was plugged into had some kind of flakey problem.  After moving my computer off of the miniswitch and plugging it directly into the router I've had no problems.  It may be that the current version of Ubuntu was more sensitive to the problem with the switch and reacted in a different way than the other OS's I've used the switch on, but I'm sure the switch itself was the core of the problem.

I have come to this realization as well. I thought that since the switch was made by Cisco it would be somewhat reliable, but alas, it was not working. I moved my port to an enterprise class switch and it works fine. Definitely something has changed, but not sure what.

---

### Post by jwest68 on 2012-02-28
One possible solution (I know this post is really old, but still I found it when searching for a similar problem) is to turn autonegotiation off. (install ethtool, then run 'ethtool -s eth0 autoneg off speed 100' or something similar)

---

### Post by EmmoSlade on 2012-07-17
Greetings,

I had a similar issue with eth0 not connecting.  Packets were being sent and received but I was getting IP of 0.0.0.0 and had similar log files.  Syslog files showed:
(eth0): device state change: 2 -> 3 (reason 40).  
(eth0): deactivating device (reason: 40).

Tried everything that I could think of.  I installed gnome-device-manager which is only a gui viewer.  You cannot uninstall devices from here.  I finally checked updates and installed the "isc-dhcp-client" and "isc-dhcp-common" updates that I had not installed yet.  This fixed my issue!!

Hope this helps...

---

### Post by wildmanne39 on 2012-07-17
Hi, thanks for sharing, the thread has been closed, please do not post in a thread that has been inactive for a year or more.
Thanks

---

