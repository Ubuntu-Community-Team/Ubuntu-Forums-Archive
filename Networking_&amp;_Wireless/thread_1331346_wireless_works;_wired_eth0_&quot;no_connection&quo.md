---
title: "wireless works; wired eth0 &quot;no connection&quot;"
date: 2009-11-19
forum: Networking &amp; Wireless
---

### Post by NutmegCT on 2009-11-19
Many thanks to you for helping me get my Broadcom 4309 card connected on my new 9.10 laptop.  I'd also like to learn how to connect via the ethernet cable.

Dell Latitude D505 with newly installed and updated 9.10.  NetMgr shows Wireless connected to Linksys router (via Broadcom 4309 card).  

If I disconnect wireless, and plug in active ethernet cable directly from the router to my laptop, NetMgr shows Wired auto eth0 - disconnected.  Can't click to connect.

I've tried sudo dhclient but no success.

Here's ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:0f:1f:a9:89:d5  
          inet6 addr: fe80::20f:1fff:fea9:89d5/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:9364 errors:0 dropped:0 overruns:0 frame:0
          TX packets:43 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:589756 (589.7 KB)  TX bytes:9123 (9.1 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:352 (352.0 B)  TX bytes:352 (352.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:90:96:a9:e9:3e  
          inet addr:192.168.1.125  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::290:96ff:fea9:e93e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1540 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1394 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1564386 (1.5 MB)  TX bytes:213482 (213.4 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-90-96-A9-E9-3E-61-39-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

(the above was done while wireless was connected, so I can stay on the forum here).

Here's ifconfig after disconnecting wireless, plugging ethernet cable, and using NetMgr to choose Wired eth0.  Network icon shows it's trying to connect, but then I get "Wired Network disconnected" in an alert window.


eth0      Link encap:Ethernet  HWaddr 00:0f:1f:a9:89:d5  
          inet6 addr: fe80::20f:1fff:fea9:89d5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12245 errors:0 dropped:0 overruns:0 frame:0
          TX packets:53 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:771641 (771.6 KB)  TX bytes:12543 (12.5 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:352 (352.0 B)  TX bytes:352 (352.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:90:96:a9:e9:3e  
          inet6 addr: fe80::290:96ff:fea9:e93e/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1553 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1396 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1568587 (1.5 MB)  TX bytes:213666 (213.6 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-90-96-A9-E9-3E-61-39-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

Ping test is successful in the wireless connection; no pings possible in wired.


Any advice will certainly be appreciated!
Thanks.
Tom in Connecticut

---

### Post by ghostborg on 2009-11-19
Just a shot in the dark , but make sure its not disabled in the bios for some reason, sometimes Ubuntu can detect hardware that is disabled. Make sure there is not a switch or soft-switch somewhere on the machine disabling it. Check that you are plugging into a lan port and not the Internet port on the router. Take a step back and ponder the obvious and hopefully thats all it is.

Good luck

---

### Post by NutmegCT on 2009-11-19
Thanks Ghost.  BIOS shows wireless is enabled, but I'm not using wireless - just e'net.  I told Ubuntu to disconnect the wireless connection, but Ubuntu won't let me click the Wired eth0 connection - it's greyed out.  

I'm using the e'net cable coming out of the cable modem; that cable works with my ibook and my Dell desktop as a direct connection.  Just seems that Ubuntu sees the ethernet (eth0) connection, but can't use it.

Tom

---

### Post by Iowan on 2009-11-19
Turn off the wireless and try the wired.  Ordinarily, Network Manager will manage only one network at a time (although when I have wired connected to my laptop, it also connects to neighbor's wireless). Otherwise, check the properties for the wired connection to see if it has "Connect automatically" enabled.

---

### Post by NutmegCT on 2009-11-19
> **Iowan said:**
> Turn off the wireless and try the wired.  Ordinarily, Network Manager will manage only one network at a time (although when I have wired connected to my laptop, it also connects to neighbor's wireless). Otherwise, check the properties for the wired connection to see if it has "Connect automatically" enabled.

Thanks Iowan.  Still no success.  Turned off wireless within BIOS.  NetMgr now shows wireless (wan1) unavailable, wired (eth0) available.  NetMgr showed "auto wan1" so I un-checked "connect automatically". 

Edit:  also made sure that eth0 (wired) is checked "connect automatically".

Click on eth0 and the netmgr icon spins slowly, then after about a minute says "Network Disconnected".

Wireless still works fine.
T.
PS  - I *think* I returned everything to situation normal, but now I've lost wireless *and* wired.   argh

---

### Post by NutmegCT on 2009-11-19
This is amazing.  I got the wireless connection running again by repeating the same Terminal commands I used yesterday (based on this forum's help).

I'm scared to actually admit this ... but it *might* be that I'm learning something.

Still no wired connection, but I'm starting to understand some really basic commands.

Tom

---

### Post by Iowan on 2009-11-19
Probably not your problem, but [this]("http://ubuntuforums.org/showthread.php?t=1156441") describes my DHCP problem.

---

### Post by NutmegCT on 2009-11-20
> **Iowan said:**
> Probably not your problem, but [this]("http://ubuntuforums.org/showthread.php?t=1156441") describes my DHCP problem.

I'd like to try that (edit the dhclient.conf), but when I try to save the edited file, I get "you're not the owner of that file" - so I can't save the revised version.  Nor can I delete or move it and save a different version.

Thanks.
Tom

---

### Post by NutmegCT on 2009-11-20
OK - found out what gksudo is for.  Got the .conf file modified, restarted, but no success.  Wireless is fine.  Turn off wireless in BIOS, restart machine, NetMgr shows Wired eth0 available (and never connected), click eth0, eth0 turns boldface, but still get "disconnected" alert.

Thanks.
Tom

---

### Post by NutmegCT on 2009-11-25
Solved.

It was totally simple.  Instead of using the ethernet cable direct from my cable modem, I left that cable plugged into the wireless router, and ran a second cable from the router to the laptop.  Wireless connection was automatic.

Can't believe it was so easy ... but sure wish I'd known that the direct cable modem ethernet connection would *not* work before I spent so much time at the Terminal!

Thanks all.
Tom

---

### Post by Iowan on 2009-11-25
Terminal time is a good thing. ;)
Glad you got it fixed!

---

