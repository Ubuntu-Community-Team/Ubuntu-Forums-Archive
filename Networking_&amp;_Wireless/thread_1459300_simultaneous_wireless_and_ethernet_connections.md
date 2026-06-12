---
title: "simultaneous wireless and ethernet connections"
date: 2010-04-21
forum: Networking &amp; Wireless
---

### Post by Hakimjo on 2010-04-21
My wireless connection to the internet via a usb antenna works fine, until I plug in an ethernet cable to connect to my printer.  As soon as ethernet is plugged in, the wireless internet connection is interrupted.  When I unplug, it is reestablished.  How can I have both connections at the same time ? (9.10)
Thanks

---

### Post by mosquetero on 2010-04-21
Can you please post the output of the command ```
ifconfig
``` in both situations? Hope I can help you

---

### Post by Hakimjo on 2010-04-21
Hola Mosquetero

these are the two results of IFCONFIG:

WIRELESS INTERNET OK - ETHERNET NOT PLUGGED:
eth1      Link encap:Ethernet  HWaddr 00:1d:7d:1e:3f:cf  
          adr inet6: fe80::21d:7dff:fe1e:3fcf/64 Scope:Lien
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Packets reçus:5180 erreurs:0 :0 overruns:0 frame:0
          TX packets:6226 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:1199807 (1.1 MB) Octets transmis:577109 (577.1 KB)
          Interruption:17 

lo        Link encap:Boucle locale  
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reçus:62119 erreurs:0 :0 overruns:0 frame:0
          TX packets:62119 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:1807493 (1.8 MB) Octets transmis:1807493 (1.8 MB)

wlan1     Link encap:Ethernet  HWaddr 00:14:a5:8e:cc:16  
          inet adr:192.168.0.2  Bcast:192.168.0.255  Masque:255.255.255.0
          adr inet6: fe80::214:a5ff:fe8e:cc16/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:142913 erreurs:0 :0 overruns:0 frame:0
          TX packets:136028 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:187291395 (187.2 MB) Octets transmis:16102463 (16.1 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-14-A5-8E-CC-16-00-00-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:0 (0.0 B) Octets transmis:0 (0.0 B)

and:

ETHERNET PLUGGED (NOTHING RUNNING OR ATTEMPTED) - WIRELESS INTERNET INTERRUPTED (but still connected to wireless router)
eth1      Link encap:Ethernet  HWaddr 00:1d:7d:1e:3f:cf  
          adr inet6: fe80::21d:7dff:fe1e:3fcf/64 Scope:Lien
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Packets reçus:5180 erreurs:0 :0 overruns:0 frame:0
          TX packets:6226 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:1199807 (1.1 MB) Octets transmis:577109 (577.1 KB)
          Interruption:17 

lo        Link encap:Boucle locale  
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reçus:62119 erreurs:0 :0 overruns:0 frame:0
          TX packets:62119 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:1807493 (1.8 MB) Octets transmis:1807493 (1.8 MB)

wlan1     Link encap:Ethernet  HWaddr 00:14:a5:8e:cc:16  
          inet adr:192.168.0.2  Bcast:192.168.0.255  Masque:255.255.255.0
          adr inet6: fe80::214:a5ff:fe8e:cc16/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:142913 erreurs:0 :0 overruns:0 frame:0
          TX packets:136028 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:187291395 (187.2 MB) Octets transmis:16102463 (16.1 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-14-A5-8E-CC-16-00-00-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:0 (0.0 B) Octets transmis:0 (0.0 B)

(hey, how do I quote in these nice scroll boxes ?)

Yours,

Joachim

---

### Post by mosquetero on 2010-04-21
To quote the small boxes you must click in the # icon when you are writing text.

Strange, I thought you may be losing the IP somehow but not the case. Maybe I am wrong but I guess that in the ethernet network your computer and printer should have an ip which in this case is not happening. Have you tried to add statically an ip address to your compuer in the wired network? Try:

```
ifconfig eth1 add 192.168.1.1 netmask 255.255.255.0
```

cheers!

---

### Post by Iowan on 2010-04-21
Does the wired work when plugged in? In both cases, eth1 never seems to have an address. Another before/after to check: **route -n** 
If all traffic is routed through wired card, wireless is effectively killed.

Is the "Available to all users" box checked on either/both?

---

### Post by lswb on 2010-04-21
If you are using Network Manager it will disable wireless when it thinks a wired ethernet connection is available. There is a way to force your system to use the ethernet for a designated ip address range e.g. your printer but I'm unsure of exactly how. You may be able to use it with /etc/network/interfaces file.

However, if your wireless network uses a router, an easier solution may be to plug your printer into one of the router ethernet ports. Most routers can be configured to assign a static ip address to one or more devices such as the printer, or in some cases the printer can be identified on your local net by a host name of some kind. Sorry I cannot provide detailed solution but maybe this info will help you in your search.

---

### Post by Hakimjo on 2010-04-22
Thank you for insights and suggestions.

Yes, the easiest would be to plug the router to the internet and the printer and all (4) computers to the router, too, either via ethernet or wireless.  The problem is that the internet only comes from a distant wireless source.  If the (linksys) router could receive and distribute internet through the wireless, the problem might be avoided.  Any idea for this ?

Yes, I use network manager.  The eth is thus connected to a router that does not have internet, only the other computers and the printer.  The wireless connection is also suspended when I connect ethernet directly to the printer, with a specific connection and static IP.  I also looked for the eth0 connection in order to cancel it, but there isn't even any eth0 in the list of wired connections.  Can I not tell Network Manager that there is no internet on eth and that it should please do what I am asking it to do ?

---

### Post by Hakimjo on 2010-04-27
I don't know how and why, but the problem disappeared.  Now, when I connect the printer on ethernet, the internet on wireless is briefly interrupted and then reestablished automatically.  May, this was fixed in one of the regular updates during the last days ?
Thanks for help.
j

---

### Post by Iowan on 2010-04-27
You may want to give it a couple of days before you mark the thread [[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").

---

### Post by qkzoo on 2011-03-21
I, too, am experiencing this issue using Maverick.  I will setup my router to assign static ip and report back.

---

