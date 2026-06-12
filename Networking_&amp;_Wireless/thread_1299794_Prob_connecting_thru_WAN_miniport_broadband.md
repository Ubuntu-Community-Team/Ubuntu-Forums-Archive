---
title: "Prob connecting thru WAN miniport broadband"
date: 2009-10-24
forum: Networking &amp; Wireless
---

### Post by munish4u911ex on 2009-10-24
HI,

I am new to linux & having trouble connecting to the internet thru my wireless(WL) network on Ubuntu 9.10, 32bit. The WL gets connected after authentication but i cant connect to internet. On windows I connect thru WAN minport (broadband) with just a password & user name. From 'Connection Information' & 'Network Tools' I found that the wireless card is recognized as Ethernet Interface 1 (eth1).

When I go to Terminal & enter "sudo pppoeconf" it says:
I found 2 Ethernet devices:
    eth0
    eth1

I press yes, & then:
 Looking for PPPoE Access Concentrator on eth1... (the WL LED blinks 4-5 times during scanning on eth1)

Sorry, I scanned 2 interfaces, but the Access
Concentrator of your provider did not respond. Please
check your network and modem cables. Another reason
for the scan failure may also be another running pppoe
process which controls the modem.

I tried to add a DSL conn. but it gives an error shown in the image:
[http://lh5.ggpht.com/_Njeu3g-Ugm0/SuMEZn5f-zI/AAAAAAAABEY/2awjkn6FQi4/s800/Screenshot-1.png](http://lh5.ggpht.com/_Njeu3g-Ugm0/SuMEZn5f-zI/AAAAAAAABEY/2awjkn6FQi4/s800/Screenshot-1.png)

See this also: [http://lh4.ggpht.com/_Njeu3g-Ugm0/SuMEZt76zeI/AAAAAAAABEg/VKYcpjyzgvk/s800/Screenshot-Devices%20-%20Network%20Tools.png](http://lh4.ggpht.com/_Njeu3g-Ugm0/SuMEZt76zeI/AAAAAAAABEg/VKYcpjyzgvk/s800/Screenshot-Devices%20-%20Network%20Tools.png)

What shud I do? I searched too much on the net but all guys were having wired connection. ](*,):(:confused:

---

### Post by munish4u911ex on 2009-10-28
Anybody not sleeping here?    :evil::lol:

---

### Post by loneowais on 2009-11-07
I have the same problem with Miniport WAN. NM and pppoe both fail to connect.

Vista fails too but XP works fine.

---

