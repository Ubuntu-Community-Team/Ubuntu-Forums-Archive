---
title: "Network going down repeatedly"
date: 2010-01-22
forum: Networking &amp; Wireless
---

### Post by karihm on 2010-01-22
Hi,
a few weeks ago I started to get problem with my wired network, it goes down after a few minutes or sometimes less than that. I first noticed this problem after new years eve and during the vacation I had configured a wireless network. 

The wireless network is working perfectly though, it's only the wired network that stops working after a short while. When invoking ifconfig I can not see any problem though and nothing in the /var/log/syslog either. 

I don't know if the problem really was caused since I configured a wireless network or if it just was a coincident that the problem occurred after that. I have also removed the wireless network and turned off the wireless network phisically on my PC (there is a button for that) but I still have the problem.

This is really annoying, can't work like this so I hope someone can help me out here!
Btw, I am using Ubuntu 9.10

---

### Post by zaphod777 on 2010-01-22
Just a thought have you tried a different eathernet cable?

---

### Post by karihm on 2010-01-22
> **zaphod777 said:**
> Just a thought have you tried a different eathernet cable?

Yes I have changed cable to a brand new one and it's connected to a switch along with other computers, for example a PC of exactly the same hardware and OS. My PC is the only one having this problem. I have also tried different ports in this switch.

---

### Post by zaphod777 on 2010-01-22
I would recommend rebooting the router and switch for at least 30 seconds. Sometimes the MAC tables can get messed up. Also I would ping your router in one window and ping a web page  like google.com in another window and see if you lose pings to the router and internet at the same time.

If you only lose internet not lan then it may be a DNS issue.

---

### Post by francisc1701 on 2010-01-22
```
dmesg | grep -i mtu
```
Does that happen to return anything at all?
You may have the same problem I had: for some reason, the MTU kept going from 1500 to 1492, back to 1500 then 1492 again, and so on forever.

If I want wired networking, I need to manually set the MTU to 1492.

---

### Post by karihm on 2010-01-22
> **zaphod777 said:**
> I would recommend rebooting the router and switch for at least 30 seconds. Sometimes the MAC tables can get messed up. Also I would ping your router in one window and ping a web page like google.com in another window and see if you lose pings to the router and internet at the same time.

If you only lose internet not lan then it may be a DNS issue.

I turned off the switch for a minute and changed port again but it didn't help. It's not a router though just a switch so I can't ping it though.

> **francisc1701 said:**
> ```
dmesg | grep -i mtu
```Does that happen to return anything at all?
You may have the same problem I had: for some reason, the MTU kept going from 1500 to 1492, back to 1500 then 1492 again, and so on forever.

If I want wired networking, I need to manually set the MTU to 1492.

No it doesn't return anything.

---

### Post by zaphod777 on 2010-01-22
What is your network layout? can you put a constant ping to your router?

---

### Post by karihm on 2010-01-22
> **zaphod777 said:**
> What is your network layout? can you put a constant ping to your router?

I am connected to a simple switch which is connected to a router. There is another PC of exactly the same model as mine running the same OS version (ubuntu 9.10) which is connected to the same switch so I am pretty sure the problem is on my PC. 

My PC worked flawlessly before Christmas but during Christmas I configured a wireless network I use at home. After new year when I came back at work I noticed this problem.

---

### Post by zaphod777 on 2010-01-22
do you have a Default gateway staticly configured on the wireless? 2 default gateways configured on your machine can defiantly cause issues packets don't know where to go. 

Can you try setting the packet size like the other poster asked and please give me the ping results? It will still help diagnose the issue even if it is isolated to your machine.

---

### Post by doas777 on 2010-01-22
when it goes out next, try pinging the router by ipaddress. does it go through? if so, try 
```
nslookup ubuntuforums.org
``` to see if it is a name resolution issue.

if the ping fails, try running 
```
sudo ethtool eth0
```

and see if everythign looks alright there (correct link speed and duplex settings, etc).
here is the output of mine (yours may vary):
```

Settings for eth0:
    Supported ports: [ TP MII ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
    Advertised auto-negotiation: Yes
    Speed: 100Mb/s
    Duplex: Full
    Port: MII
    PHYAD: 0
    Transceiver: internal
    Auto-negotiation: on
    Current message level: 0x00000007 (7)
    Link detected: yes

```

---

### Post by lukjad on 2010-01-22
How old is the router? I have had problems very similar to this and it just turned out that the router was dying a slow death. At the end of two months I could not even get onto the internet at all. If possible, try using another router and seeing if that happens.

---

### Post by karihm on 2010-01-22
> **zaphod777 said:**
> do you have a Default gateway staticly configured on the wireless? 2 default gateways configured on your machine can defiantly cause issues packets don't know where to go. 

Can you try setting the packet size like the other poster asked and please give me the ping results? It will still help diagnose the issue even if it is isolated to your machine.

Both the wireless and wired networks are using DHCP. I have also removed the wireless network and turned off the wireless network physically using a button on my PC.

I don't know how to set the packet size and the grep didn't return anything.

> **doas777 said:**
> when it goes out next, try pinging the router by ipaddress. does it go through? if so, try 
```
nslookup ubuntuforums.org
``` to see if it is a name resolution issue.

if the ping fails, try running 
```
sudo ethtool eth0
```and see if everythign looks alright there (correct link speed and duplex settings, etc).
here is the output of mine (yours may vary):
```

Settings for eth0:
    Supported ports: [ TP MII ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
    Advertised auto-negotiation: Yes
    Speed: 100Mb/s
    Duplex: Full
    Port: MII
    PHYAD: 0
    Transceiver: internal
    Auto-negotiation: on
    Current message level: 0x00000007 (7)
    Link detected: yes

```

The nslookup works when the network is down, it uses a DNS server locally at my company and the result is:

Non-authoritative answer:
Name:    ubuntuforums.org
Address: 91.189.94.12

Also tried this as you suggested:
$ sudo ethtool eth0
Settings for eth0:
    Supported ports: [ TP ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Full 
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Full 
    Advertised auto-negotiation: Yes
    Speed: 100Mb/s
    Duplex: Full
    Port: Twisted Pair
    PHYAD: 1
    Transceiver: internal
    Auto-negotiation: on
    Supports Wake-on: pumbag
    Wake-on: g
    Current message level: 0x00000001 (1)
    Link detected: yes

---

### Post by doas777 on 2010-01-22
> **karihm said:**
> 

The nslookup works when the network is down, it uses a DNS server locally at my company and the result is:

Non-authoritative answer:
Name:    ubuntuforums.org
Address: 91.189.94.12

well that means that your network is not actually "down" but that you are having a problem either in software or in an intermediary device like a gateway router. can you do a tracert to google when it is working, and another when it is not to compare? you may also want to run route next time it goes down, and make sure you can still ping all your local gateways.

---

### Post by karihm on 2010-01-22
> **lukjad007 said:**
> How old is the router? I have had problems very similar to this and it just turned out that the router was dying a slow death. At the end of two months I could not even get onto the internet at all. If possible, try using another router and seeing if that happens.

I don't know much about the router but this is within a company and the router works for everybody else. The IT support cannot help me though since Ubuntu is not supported.

> **doas777 said:**
> well that means that your network is not actually "down" but that you are having a problem either in software or in an intermediary device like a gateway router. can you do a tracert to google when it is working, and another when it is not to compare? you may also want to run route next time it goes down, and make sure you can still ping all your local gateways.

I did a traceroute using the network tools in the System->Administration menu and the result is the same both when the network is working and not. I get a list with 32 rows, the first row display my PCs IP as hostname and IP and time aprox 0.3 ms. The other rows displays "no" as hostname, "reply" as IP and "*" as Time.

---

### Post by doas777 on 2010-01-22
what is the output of 
'route'

---

### Post by karihm on 2010-01-22
I set up a continuous ping on the internal IP of my router, i.e. my default route, and google.com as suggested earlier and since then my network worked for some 10 minutes which is much longer than usual. Then it suddenly stopped again and I have no idea if the improvement had anything to do with the ping or perhaps that some colleagues went home.

When the network connection died both pings stopped. Now when typing this the ping on the default route started again but not the ping on google, and I cannot browse any web pages. To be able to post this I have to manually connect using the network icon.


> **doas777 said:**
> what is the output of 
'route'

This is the output both when the network works and not.

$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
172.16.128.0    *               255.255.255.128 U     1      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         172.16.128.118  0.0.0.0         UG    0      0        0 eth0

Edit: added info about route above

---

### Post by karihm on 2010-01-25
Any more ideas about this or do I have to re install ubuntu?

---

### Post by doas777 on 2010-01-25
well, it looks like your host is working properly, so i would start looking beyond it to the gateways. the problem could be software abheration (a reinstall might address it) but it may as well be a problem upstream.

---

### Post by karihm on 2010-01-25
> **doas777 said:**
> well, it looks like your host is working properly, so i would start looking beyond it to the gateways. the problem could be software abheration (a reinstall might address it) but it may as well be a problem upstream.

I cannot see how the problem could be outside my PC since my colleague have exactly the same model of the PC and exactly the same OS (Ubuntu 9.10) and it works perfectly for him. There are also a lot of other Windows PCs that works flawlessly.

---

### Post by doas777 on 2010-01-25
> **karihm said:**
> I cannot see how the problem could be outside my PC since my colleague have exactly the same model of the PC and exactly the same OS (Ubuntu 9.10) and it works perfectly for him. There are also a lot of other Windows PCs that works flawlessly.
then I would compare your config with your colleague's line by line.
also it may just be a firefox issue, so you could just try reinstalling it, or cleaning it with bleachbit.

---

### Post by karihm on 2010-01-26
> **doas777 said:**
> then I would compare your config with your colleague's line by line.
also it may just be a firefox issue, so you could just try reinstalling it, or cleaning it with bleachbit.

What configuration files should I compare?
It's not just a firefox issue though, it affects ping also.

---

### Post by doas777 on 2010-01-26
> **karihm said:**
> What configuration files should I compare?
It's not just a firefox issue though, it affects ping also.

but you said earlier that while you were down, you could ping and nslookup google (see post #12). if that is still the case, then yes it is a software issue. can you please clarify?

---

### Post by karihm on 2010-02-04
> **doas777 said:**
> but you said earlier that while you were down, you could ping and nslookup google (see post #12). if that is still the case, then yes it is a software issue. can you please clarify?

No I never said that at post #12 I only said nslookup worked. At post #16 I also said this:

> **karihm said:**
> When the network connection died both pings stopped. Now when typing this the ping on the default route started again but not the ping on google, and I cannot browse any web pages. To be able to post this I have to manually connect using the network icon.

I.e. both pings stopped but after a while the ping on the default route started to work again but nit the ping on google. 

To me this seems to indicate a problem outside my PC since ping on default route worked but I could not access anything outside. However, I am the only onhe having this problem. An other PC of exactly the same hardware and software works flawlessly as well as many windows PCs.

Right now the situation is the same, ping on default route works but not ping on google. Tried netstat and it just hang several seconds before I got the response on it. Tried netstat once more and now it responds immediatly even though the condition on the pings is the same, i,e, default route works but not google.

---

### Post by europa on 2010-02-07
Hi Karihm,

I'm experiencing the same issue.  My network is working for about a minute and then everything goes down.  Ubuntu says i'm still connected but I cannot ping default gateway and all other network activity just stops.

This only happens on this new acer laptop i recently purchased. lspci shows:

```
jack@jack-laptop:~$ lspci | grep Ethernet
08:00.0 Ethernet controller: Attansic Technology Corp. Atheros AR8132 / L1c Gigabit Ethernet Adapter (rev c0)
```

If I use NetworkManager to disable/enable network it comes back up.... but only for another minute.

Here is my output from ping:
```
jack@jack-laptop:~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=0.254 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=0.391 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=0.298 ms
64 bytes from 192.168.1.1: icmp_seq=4 ttl=64 time=0.340 ms
64 bytes from 192.168.1.1: icmp_seq=5 ttl=64 time=0.354 ms
64 bytes from 192.168.1.1: icmp_seq=6 ttl=64 time=0.369 ms
64 bytes from 192.168.1.1: icmp_seq=7 ttl=64 time=0.396 ms
64 bytes from 192.168.1.1: icmp_seq=8 ttl=64 time=0.379 ms
64 bytes from 192.168.1.1: icmp_seq=9 ttl=64 time=0.350 ms
64 bytes from 192.168.1.1: icmp_seq=10 ttl=64 time=0.359 ms
64 bytes from 192.168.1.1: icmp_seq=11 ttl=64 time=0.325 ms
64 bytes from 192.168.1.1: icmp_seq=12 ttl=64 time=0.322 ms
64 bytes from 192.168.1.1: icmp_seq=13 ttl=64 time=0.417 ms
64 bytes from 192.168.1.1: icmp_seq=14 ttl=64 time=0.365 ms
64 bytes from 192.168.1.1: icmp_seq=15 ttl=64 time=0.365 ms
64 bytes from 192.168.1.1: icmp_seq=16 ttl=64 time=0.320 ms
64 bytes from 192.168.1.1: icmp_seq=17 ttl=64 time=0.388 ms
64 bytes from 192.168.1.1: icmp_seq=18 ttl=64 time=0.354 ms
64 bytes from 192.168.1.1: icmp_seq=19 ttl=64 time=0.327 ms
64 bytes from 192.168.1.1: icmp_seq=20 ttl=64 time=0.353 ms
64 bytes from 192.168.1.1: icmp_seq=21 ttl=64 time=0.332 ms
64 bytes from 192.168.1.1: icmp_seq=22 ttl=64 time=0.387 ms
64 bytes from 192.168.1.1: icmp_seq=23 ttl=64 time=0.380 ms
64 bytes from 192.168.1.1: icmp_seq=24 ttl=64 time=0.432 ms
64 bytes from 192.168.1.1: icmp_seq=25 ttl=64 time=0.334 ms
64 bytes from 192.168.1.1: icmp_seq=26 ttl=64 time=0.424 ms
64 bytes from 192.168.1.1: icmp_seq=27 ttl=64 time=0.413 ms
64 bytes from 192.168.1.1: icmp_seq=28 ttl=64 time=0.429 ms
64 bytes from 192.168.1.1: icmp_seq=29 ttl=64 time=0.441 ms
64 bytes from 192.168.1.1: icmp_seq=30 ttl=64 time=0.449 ms
64 bytes from 192.168.1.1: icmp_seq=31 ttl=64 time=0.428 ms
64 bytes from 192.168.1.1: icmp_seq=32 ttl=64 time=0.503 ms
64 bytes from 192.168.1.1: icmp_seq=33 ttl=64 time=0.352 ms
64 bytes from 192.168.1.1: icmp_seq=34 ttl=64 time=0.354 ms
64 bytes from 192.168.1.1: icmp_seq=35 ttl=64 time=0.356 ms
64 bytes from 192.168.1.1: icmp_seq=36 ttl=64 time=0.364 ms
64 bytes from 192.168.1.1: icmp_seq=37 ttl=64 time=0.689 ms
From 192.168.1.4 icmp_seq=88 Destination Host Unreachable
From 192.168.1.4 icmp_seq=89 Destination Host Unreachable
From 192.168.1.4 icmp_seq=90 Destination Host Unreachable
From 192.168.1.4 icmp_seq=91 Destination Host Unreachable
From 192.168.1.4 icmp_seq=92 Destination Host Unreachable
From 192.168.1.4 icmp_seq=93 Destination Host Unreachable
From 192.168.1.4 icmp_seq=94 Destination Host Unreachable
From 192.168.1.4 icmp_seq=95 Destination Host Unreachable
From 192.168.1.4 icmp_seq=96 Destination Host Unreachable
^C
--- 192.168.1.1 ping statistics ---
97 packets transmitted, 37 received, +9 errors, 61% packet loss, time 96092ms
rtt min/avg/max/mdev = 0.254/0.380/0.689/0.074 ms, pipe 3
jack@jack-laptop:~$ 

```

---

### Post by Guilden_NL on 2010-03-07
Europa,
I am having the same problem with my son's Acer laptop on my home network.  All of our many systems work wireless and cabled, everything runs Ubuntu except for a few RHEL 5.4 servers and a Sun server.

I'll follow this thread because I am scratching my head.  It started somewhere around 8.04, but may have been with Intrepid.  He uses his HP Mini MIE mostly, so I forgot about it until I tried to use his Acer tonight.

I've tracked it down to when there is a lot of activity like when I run a traceroute, ping, or run a lot of pings across many servers (finding the best update server.)..

---

### Post by europa on 2010-03-08
I ended up switching to fedora and everything runs great now!

---

