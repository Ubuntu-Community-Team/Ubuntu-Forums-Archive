---
title: "Internet Sharing wiht two ubuntu 8.10 boxes"
date: 2008-12-17
forum: Networking &amp; Wireless
---

### Post by Dwiman89 on 2008-12-17
Hey.
Im tring to get internet sharing on two ubuntu 8.10 boxes via crossover cable. I have tried this before with ubuntu as the gateway hosting the internet to a Mac, but the mac bricked before someone on here could finish showing me how to set it up. i can even get a ping between the two comps with this configuration.....

Comp1(one with the wireless internet);

set to manual static
IP;    192.168.0.1
subnet 255.255.255.0
and gateway is blank.
broadcast 192.168.0.255(it gets this itself, I dont know what it is or where it came from)

Comp2(one that needs the internet)

manual static
IP;        192.168.0.2
subnet;    255.255.255.0
gateway;   192.168.0.1
broadcast; 192.168.0.255(where ever that comes from...)

I am unable to simply get a ping across the two comps with this set... 

"From 192.168.0.1 icmp_seq=7 Destination Host Unreachable
^C
--- 192.168.0.2 ping statistics ---
7 packets transmitted, 0 received, +6 errors, 100% packet loss, time 6016ms
, pipe 3"

And no I dont want to go buy a router, I only have two comps, and I already have a crossover cable.

can someone please help me?

---

### Post by Iowan on 2008-12-17
I presume you've seen the help page on [ICS]("https://help.ubuntu.com/community/Internet/ConnectionSharing"). There's also a [workaround]("http://ubuntuforums.org/showthread.php?t=974382") for a static address bug.

---

### Post by Dwiman89 on 2008-12-17
Someone said somewhere that you can use firestarter to set up ICS with DHCP, That would bypass the gnome bug... I dont like the idea of deleting nm... even though it has the static bug, it works nice for my wireless and whatnot...

---

### Post by Dwiman89 on 2008-12-18
I tried firestarter( I like the idea of DHCP). it wont work though, I have wlan0 as my internet, and eth1 as my local netwrok. when I try to start it, it says; "failed to start firewall". The Device eth1 is not ready. Please check your network device settings and make sure your internet connection is active"


any ideas?

---

### Post by Dwiman89 on 2008-12-18
> **Iowan said:**
> I presume you've seen the help page on [ICS]("https://help.ubuntu.com/community/Internet/ConnectionSharing"). There's also a [workaround]("http://ubuntuforums.org/showthread.php?t=974382") for a static address bug.


I followed the instructions at that ICS link and I still am unable to get a ping through to anywhere...

---

