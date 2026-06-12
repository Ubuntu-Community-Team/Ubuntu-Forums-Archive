---
title: "Wired Connection Cannot Obtain IP Address"
date: 2009-08-28
forum: Networking &amp; Wireless
---

### Post by archeryguru2000 on 2009-08-28
Hello all, I have a small problem with my network connectivity.  My wireless is working just fine, but my wired connection is unable to obtain an IP address.  I have no clue how long this has been an issue as I generally use only my wireless (laptop).

However, I recently have tried to set up a connection to a couple of network printers through a wired connection and was not able to succeed.  I have Wicd as my network manager, and upon plugging in my ethernet cable, a wired option becomes available for network connections.  I choose connect... and wait.  Eventually, a pop-up window is displays that states an ip address could not be obtained.

Here's a few CLI outputs for added info:
```

$: lspci -nn | grep 'Ethernet'
00:0a.0 Ethernet controller [0200]: nVidia Corporation MCP67 Ethernet [10de:054c] (rev a2)
03:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter [168c:001c] (rev 01)

```
```
$: ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:1e:68:46:88:6b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:5962 (5.9 KB)
          Interrupt:252 Base address:0xc000 

```
```

$: cat /etc/network/interfaces
auto lo
iface lo inet loopback

```

Please let me know if there's any other information I may provide that could be of use.

I appreciate any assistance that anybody may have to help me get my wired connection up and running.

Thanks,
~~archery~~

---

### Post by Iowan on 2009-08-28
I keep hoping to solve problems with [this]("http://ubuntuforums.org/showthread.php?t=1156441") thread - it sometimes helps, usually not. Since your wireless is working (through the same router?) it probably won't help.

---

### Post by archeryguru2000 on 2009-08-28
Sorry Iowan, I've already tried those suggestions... no such luck.  I'm not even sure where else to look.  I've been trying many solutions from multiple forums for two days now.  I've found out however, that I seem to be having some troubles connecting to secured networks also (incase that information is valuable to someone).

Thanks anyway though,
~~archery~~

---

### Post by izziere on 2009-08-29
Your interfaces file looks very light.  It could be the network manager you are using.  I stopped using the network managers with *buntu and resorted to manual configurations, as it kept screwing up my systems.

You might want to try configuring eth0 and your wireless network via interfaces.  There are plenty of threads on that subject - am in a rush, otherwise I would giver fuller response.

May also be a problem with router?  Do you have security settings activated on router that may prevent certain devices/addresses from registering?

---

### Post by archeryguru2000 on 2009-08-29
> **izziere said:**
> Your interfaces file looks very light.  It could be the network manager you are using.  I stopped using the network managers with *buntu and resorted to manual configurations, as it kept screwing up my systems.

You might want to try configuring eth0 and your wireless network via interfaces.  There are plenty of threads on that subject - am in a rush, otherwise I would giver fuller response.

May also be a problem with router?  Do you have security settings activated on router that may prevent certain devices/addresses from registering?

I do agree with you on the network manager.  I have used the wired network here (at work) before, but I think it might have been with a different network manager (Gnome's network-manager).  However, why should my current network manager (Wicd, btw) be any different?  I would assume that any/all network managers do basically the same thing... right?  :confused:  Besides, as long as my encryption settings are the same (from one manager to the next), the modem/router shouldn't see any difference in what is trying to connect to it... right?

I don't know, maybe I'm completely wrong in my thinking here (wouldn't be the first OR the last :P ).

By the way, I've tried configuring my eth0 a couple of times (threads form here as well as other forums), but no such luck.  Monday I will try reinstalling Gnome's network-manager and see if that changes anything.  I'll keep everyone posted.

Thanks,
~~archery~~

---

### Post by Iowan on 2009-08-29
Have you tried manually running **dhclient**?

---

### Post by archeryguru2000 on 2009-08-31
> **Iowan said:**
> Have you tried manually running **dhclient**?

Yep, these are results of running it just now.

```

$: sudo dhclient
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/pan0/5e:b1:ce:09:e2:6c
Sending on   LPF/pan0/5e:b1:ce:09:e2:6c
Listening on LPF/wlan0/00:1f:3a:a4:4e:76
Sending on   LPF/wlan0/00:1f:3a:a4:4e:76
Listening on LPF/wmaster0/
Sending on   LPF/wmaster0/
Listening on LPF/eth0/00:1e:68:46:88:6b
Sending on   LPF/eth0/00:1e:68:46:88:6b
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

And to be honest, I'm not really sure what to make of these returns.  I understand that 'No DHCPOFFERS received.' implies that there's no return signal when trying to send/receive network messages... but that's pretty much the extent of my knowledge.

I'm getting ready to re-install Gnome's network manager now.  I'll return with my progress... or lack there of.

~~archery~~

---

### Post by archeryguru2000 on 2009-08-31
Alright, I'm back online with Gnome's Network-Manager.  However, still no wired connection.  I do not get much feedback with this manager on where the progress is halting but with a similar amount of time that is passing as before (~20-30 sec), I would assume it is still unable to obtain an IP address.

Boy this is frustrating.   :(   I think I will retry all of the previous commands that I had tried with Wicd to see if there's any difference.

~~archery~~

---

### Post by archeryguru2000 on 2009-08-31
Ok, here's the commands and their respective returns:
```

$: sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth0/00:1e:68:46:88:6b
Sending on   LPF/eth0/00:1e:68:46:88:6b
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
$: netstat -nr
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
0.0.0.0         0.0.0.0         0.0.0.0         U         0 0          0 eth0
$: route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
link-local      *               255.255.0.0     U     0      0        0 eth0
default         *               0.0.0.0         U     1000   0        0 eth0
$: sudo ifdown eth0
ifdown: interface eth0 not configured
$: sudo ifup eth0
Ignoring unknown interface eth0=eth0.
$: ping -c 4 google.com
ping: unknown host google.com

```
Can anybody make any sense of this?  I'm certain there has to be a way around this.  Sooo many other computers are on this network it isn't even funny.  I am currently sharing this office with an udergrad and his Windoze machine connected to the wired network without a hitch.  He simply plugged in the cable, his computer requested an IP address and... ***tada*** internet access.

I'll do some more searching.   :roll: 
~~archery~~

---

### Post by thestigmatic on 2009-09-08
any updates? this is killing me...

---

### Post by archeryguru2000 on 2009-09-10
> **thestigmatic said:**
> any updates? this is killing me...

I have nothing to report as far as progress is concerned.  I have no clue why I cannot connect to the wired network here.  I've tried other networks (parents house, for example) with zero problems... but with a secure network I cannot connect.  Wireless works just fine, but no wired connection.

This is kinda humorous.  Several years ago, when I first gave Linux a try, I couldn't get my wireless working and could only use wired connections.  Now it seems as though the opposite is happening.

I find it hard to believe that nobody else out there has had this problem before.  Maybe I'm just a pioneer in wired networks now.  :P

~~archery~~

---

### Post by thestigmatic on 2009-09-10
well, please keep me/us posted. if i find anything that seems to work for me, i'll be sure to do the same.

---

### Post by him610 on 2009-12-04
Did you ever get your wired connection problem solved? I encountered the same problem on my Shuttle SN68SG2 system a couple of releases ago. I kluged a workaround by using a USB 10/100 network adapter, not really satisfied with it though because one expects the onboard devices to work. I believe it caused is the MCP67 controller firmware.

---

### Post by him610 on 2009-12-05
After some investigation last night, I have concluded I have a configuration problem on my system, and it is not due to any problem with MCP67. I dug up my old Ubuntu 9.04 AMD64 Live CD and rebooted a couple of times. 
With the Cat 5 cable connected, it booted right up with the wired connection obtaining a valid IP address without delay; enabled wireless connection and it obtained an IP address without delay.
I then rebooted without the Cat 5 cable connected with the wireless connection acquiring an IP address without delay. Reconnected the Cat 5 cable, but failed to acquire an IP address.
Looks as if I need to work some more on solving my configuration problem.

Cheers.

---

### Post by Commanderdot on 2010-01-13
I have the same problem with my wired connection. It started connecting and disconnecting at intervals; and now it just dosen't even try to connect.
If I discover something I'll post it here. ;)

---

### Post by archeryguru2000 on 2010-02-19
Hey everybody.  Good news... kinda.  I can connect to the wired network here.  However, it was only by shear curiosity that I even checked.  I've been using wireless here since last summer.  And one day last week I decided to plug into the wired network and instant connection.  I do not remember seeing any network-manager updates recently, but I could've over looked one.  I will have to mark this thread as solved, even though it's really only closed... the question was never truly answered.

Thanks for all your assistance,
~~archery~~

---

