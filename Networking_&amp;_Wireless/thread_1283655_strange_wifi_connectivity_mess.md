---
title: "strange wifi connectivity mess"
date: 2009-10-05
forum: Networking &amp; Wireless
---

### Post by Knacker on 2009-10-05
Hi all you helpful people. I've got a problem and I think it's in part of my own creation, so I'm going to stop trying to fix it myself and ask for some expert help. I'm a real non-expert myself, so please be generous and forgive my stupidity in advance. 

The backstory:
A couple of days ago, I was fiddling around with samba and ftp, playing with different ways of transfering files. As I was setting up an ftp server one of my computers, things got wacky. I set up port forwarding for port 21 on my router and finally got things working. Uploaded/downloaded a couple of test files and all was well and then suddenly I found that my user/sudo password on the machine running the ftp server stopped working. Well, I freaked out a bit and shut all network activity down. I was eventually able to log back in as "root" with my old user password. I was paranoid and did a bunch of rootkit scans (did someone change my password?) and changed all my passowords and etc. and all seemed well. Couldn't figure out what had happened. I was messing with so many different things (all of which seemed fine until the password weirdness) that I can't isolate what I have screwed up.  

The problem:
I don't know if it's connected at all or if I even understand what that was about, but ever since then, my wireless connection keeps pooping out and then can't reconnect. There are also pan0 and pan0-avahi and wlan0-avahi entries when i check ifconfig that I don't remember being there and have no idea about. I really don't know what the problem is or how to trouble shoot this. Can anyone suggest what this might be? Any ideas how I can fix this?

Sorry for the (possibly unnecessarily..?) long question. Many thanks in advance for any ideas/help!

---

### Post by Knacker on 2009-10-05
here's what i get from ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:30:1b:48:0c:f6  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:54079632 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15291287 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2511803488 (2.5 GB)  TX bytes:1091106047 (1.0 GB)
          Interrupt:17 

eth0:avahi Link encap:Ethernet  HWaddr 00:30:1b:48:0c:f6  
          inet addr:169.254.6.61  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:70397 errors:0 dropped:0 overruns:0 frame:0
          TX packets:70397 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:14809079 (14.8 MB)  TX bytes:14809079 (14.8 MB)

pan0      Link encap:Ethernet  HWaddr 7e:87:cb:3a:c1:c1  
          inet6 addr: fe80::7c87:cbff:fe3a:c1c1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2326 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:495847 (495.8 KB)

pan0:avahi Link encap:Ethernet  HWaddr 7e:87:cb:3a:c1:c1  
          inet addr:169.254.9.149  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

wlan0     Link encap:Ethernet  HWaddr 00:c0:ca:1d:c9:92  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:34096 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24120 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:35937895 (35.9 MB)  TX bytes:2518596 (2.5 MB)

wlan0:avahi Link encap:Ethernet  HWaddr 00:c0:ca:1d:c9:92  
          inet addr:169.254.8.170  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

wmaster0  Link encap:UNSPEC  HWaddr 00-C0-CA-1D-C9-92-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


ALSO:
The router I'm connecting to uses mac filtering and wpa encryption for security. Both of the MAC filtering and the WPA are sort of new and might be the problem...but then why would it work sometimes and then stop?

---

### Post by Knacker on 2009-10-05
okay. i think (hope) i've got a new lead on why wifi keeps crapping out (realtek 8187L + WPA), but I still don't know what all those pan0 and :avahi entries in my ifconfig are about. can someone explain what those are? thanks again!

---

### Post by t0mppa on 2009-10-05
PAN is Personal Area Network, ie. Bluetooth.

Avahi on the other hand is an implementation of Apple Zeroconf specification, which means it's used for easy plug'n'pray type of connectivity, when there's no sophisticated networking equipment (routers/hubs/switches) around. So, basically what's happening is that you're not getting connected with your router and thus Avahi kicks in thinking you're trying something like a cross-over cable connection with another computer, where no third party assigns IPs.

---

