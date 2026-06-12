---
title: "Toshiba Satellite Laptop - No Wireless"
date: 2010-05-18
forum: Networking &amp; Wireless
---

### Post by Daniel9 on 2010-05-18
I did a clean install of 10.04 on my Toshiba Satellite laptop, but I cannot make a wireless connection.  The icon on the panel spins round and round, but that's it.  After a few minutes I will get a message that the wireless network is disconnected.  Any ideas?  Thanks!

---

### Post by webtechquery on 2010-05-18
Hi..

just wanted to share something.. i also have toshiba satellite. days back, when I purchased it, i was new to it so I dint notice that theres a wireless button near the volume (im not talking about ubuntu, but actually hardware).. after making alot of search.. i suddenly saw that the wireless button was off.. (the button is before the sound volume, below the mouse buttons of the keyboard)

hope this is not with ur case..

take care

---

### Post by lisati on 2010-05-18
On my Toshiba laptop, there's a switch on the front, but I don't think that's related to the problem that Daniel's experiencing. When my wireless adapter is switched off, it doesn't even "see" any wireless networks let alone spin its wheels. 

Are you able to get to Preferences->Network connections?

---

### Post by Daniel9 on 2010-05-18
The wireless button is on the side of my laptop and it is on.  Yes, I can access Preferences>Network Connections.

---

### Post by Daniel9 on 2010-05-20
So, is this a lost cause?:(

---

### Post by dubvibrations on 2010-07-22
Had the same problem on a satellite m100 - found this and it is working

Open your **Firefox** and type about:config  at URL address bar and hit enter. To make a False into True, select the  line to change, and double click. On the 2nd option change, right click  and select Modify
 - network.http.pipelining > Make it True
 - network.http.pipelining.maxrequests > Make it 8 or 10
 - network.http.proxy.pipelining > Make it True
 - network.dns.disableIPv6 > Make it True


 I'm still getting some intermittent dropouts in the wireless connection and its more of a dial up experience but at least I'm not tethered to the router..

---

### Post by Daniel9 on 2010-07-23
Thanks for the tip.  I've decided to stay with 9.10 until something "for sure" is resolved.

---

### Post by kolibri on 2010-09-15
I'm also having this problem, trying to resurrect an old Toshiba Portege 3500 with ubuntu 10.04.1.

Had display issues, had to add an xorg.conf file, found good instructions for that here.  but  I can't get the wireless to connect. It sees the available wireless networks, but it won't connect.

Not sure what the relevant output from lshw is,  I could hook the laptop up to ethernet and copy it all if that is necessary.

If someone could help me with this, what besides the output from lshw would you need?

---

### Post by drpjkurian on 2010-09-15
Hi
if it can sense the wireless and is not able to connect, then it should be due to secured wireless connection,Passwors and settings changes according to ISP

---

### Post by kolibri on 2010-09-15
No security on this network, it's a guest unsecured network.

here is a hand full of helpful output?
> 
owl@owl:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:08:0d:a0:cd:64  
          inet addr:131.215.71.182  Bcast:131.215.71.255  Mask:255.255.255.0
          inet6 addr: fe80::208:dff:fea0:cd64/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11646 errors:0 dropped:0 overruns:3 frame:3
          TX packets:4469 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13224109 (13.2 MB)  TX bytes:458358 (458.3 KB)

eth1      Link encap:Ethernet  HWaddr 00:02:2d:b3:7d:40  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 Base address:0x180 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:316 errors:0 dropped:0 overruns:0 frame:0
          TX packets:316 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:24976 (24.9 KB)  TX bytes:24976 (24.9 KB)


> 
owl@owl:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:"School Registered"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: None   
          Bit Rate:11 Mb/s   Sensitivity:1/0  
          Retry limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-122 dBm  Noise level=-122 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:7
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



---

### Post by perspectoff on 2010-09-15
I had the same problems. I ended up removing Network Manager and installing Wicd instead. Everything works since doing that. I have 3 Toshiba Satellites.

---

### Post by kolibri on 2010-09-15
> **perspectoff said:**
> I had the same problems. I ended up removing Network Manager and installing Wicd instead. Everything works since doing that. I have 3 Toshiba Satellites.

Ok, I'm trying wicd- with the latest version 1.7 something, it would always give me an authentication failure..  So installed 1.6.2.2 as some have suggested elsewhere, and it makes it past authentication, but hangs at obtaining IP and then gives me the error message unable to get IP.  I can connect to my neighbors unprotected network, however.

should i try to troubleshoot 1.7, or 1.6?

---

### Post by kolibri on 2010-09-15
more info- from the wicd log
(I've also purged every variation of network-manager I could find in these help threads)

log from successful  unsuccessful connection to to mysecured wireless
> 
2010/09/15 01:22:09 :: Connecting to wireless network ____Web
2010/09/15 01:22:09 :: attempting to set hostname with dhclient
2010/09/15 01:22:09 :: using dhcpcd or another supported client may work better
2010/09/15 01:22:10 :: attempting to set hostname with dhclient
2010/09/15 01:22:10 :: using dhcpcd or another supported client may work better
2010/09/15 01:22:10 :: Putting interface down
2010/09/15 01:22:10 :: Releasing DHCP leases...
2010/09/15 01:22:10 :: attempting to set hostname with dhclient
2010/09/15 01:22:10 :: using dhcpcd or another supported client may work better
2010/09/15 01:22:10 :: Setting false IP...
2010/09/15 01:22:10 :: Stopping wpa_supplicant
2010/09/15 01:22:10 :: Flushing the routing table...
2010/09/15 01:22:10 :: Putting interface up...
2010/09/15 01:22:12 :: Attempting to authenticate...
2010/09/15 01:22:48 :: wpa_supplicant authentication may have failed.
2010/09/15 01:22:48 :: connect result is Failed
2010/09/15 01:22:48 :: exiting connection thread
2010/09/15 01:22:48 :: Sending connection attempt result bad_pass
2010/09/15 01:22:49 :: attempting to set hostname with dhclient
2010/09/15 01:22:49 :: using dhcpcd or another supported client may work better
2010/09/15 01:22:49 :: attempting to set hostname with dhclient
2010/09/15 01:22:49 :: using dhcpcd or another supported client may work better
successful connection to neighbors unsecured wireless (sorry neighbor)
> 
2010/09/15 01:25:59 :: Connecting to wireless network linksys
2010/09/15 01:25:59 :: attempting to set hostname with dhclient
2010/09/15 01:25:59 :: using dhcpcd or another supported client may work better
2010/09/15 01:26:00 :: attempting to set hostname with dhclient
2010/09/15 01:26:00 :: using dhcpcd or another supported client may work better
2010/09/15 01:26:00 :: Putting interface down
2010/09/15 01:26:00 :: Releasing DHCP leases...
2010/09/15 01:26:00 :: attempting to set hostname with dhclient
2010/09/15 01:26:00 :: using dhcpcd or another supported client may work better
2010/09/15 01:26:00 :: Setting false IP...
2010/09/15 01:26:00 :: Stopping wpa_supplicant
2010/09/15 01:26:00 :: Flushing the routing table...
2010/09/15 01:26:00 :: Putting interface up...
2010/09/15 01:26:03 :: Running DHCP with hostname owl
2010/09/15 01:26:03 :: attempting to set hostname with dhclient
2010/09/15 01:26:03 :: using dhcpcd or another supported client may work better
2010/09/15 01:26:03 :: Internet Systems Consortium DHCP Client V3.1.3
2010/09/15 01:26:03 :: Copyright 2004-2009 Internet Systems Consortium.
2010/09/15 01:26:03 :: All rights reserved.
2010/09/15 01:26:03 :: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
2010/09/15 01:26:03 :: 
2010/09/15 01:26:03 :: Listening on LPF/eth1/00:02:2d:b3:7d:40
2010/09/15 01:26:03 :: Sending on   LPF/eth1/00:02:2d:b3:7d:40
2010/09/15 01:26:03 :: Sending on   Socket/fallback
2010/09/15 01:26:07 :: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
2010/09/15 01:26:08 :: DHCPOFFER of 192.168.1.113 from 192.168.1.1
2010/09/15 01:26:08 :: DHCPREQUEST of 192.168.1.113 on eth1 to 255.255.255.255 port 67
2010/09/15 01:26:08 :: DHCPACK of 192.168.1.113 from 192.168.1.1
2010/09/15 01:26:08 :: bound to 192.168.1.113 -- renewal in 33253 seconds.
2010/09/15 01:26:08 :: DHCP connection successful
2010/09/15 01:26:08 :: not verifying
2010/09/15 01:26:08 :: Connecting thread exiting.
2010/09/15 01:26:08 :: Sending connection attempt result Success
]

---

### Post by kolibri on 2010-09-15
I have one file in my /var/lib/wicd/configurations folder:

00e098f09e2c 

ap_scan=1
ctrl_interface=/var/run/wpa_supplicant
network={
       ssid="KWeb"
       scan_ssid=0
       key_mgmt=NONE
       wep_key0=8131630000
       wep_tx_keyidx=0
       priority=5
}

It has the correct network name, and the correct wep key.

---

### Post by kolibri on 2010-09-16
I'm stuck by the fact that using Wicd, I can connect to unsecured networks, but continually get the bad password message for my secured wireless.  I read that in an other thread, that some older cards have a conflict between where encryption is done, but I couldn't get the exact instructions on that thread to work for me.

I have an older generic (I guess) pcmcia card, the orinoco_cs driver is working.

would love to get working networking going.

---

### Post by kolibri on 2010-09-18
well, I had one glorious day of connectivity, not even sure what I did to make it connect, after a frustrating night of attempts, i shut the computer down, when I started it in the morning, it connected at startup to my encrypted home network, restarted it several times yesterday, it stayed connected- got my security/cat cam up and running, and when I tried to restart it today, it won't connect to my home network,  says bad password again, but will connect to neighbors unsecured network. Last thing i did two days ago was to try to install pcmcia-utils, but it said they already were installed.

---

