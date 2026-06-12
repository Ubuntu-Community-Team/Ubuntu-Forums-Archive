---
title: "No connection with ubuntu"
date: 2010-05-18
forum: Networking &amp; Wireless
---

### Post by Migaz91 on 2010-05-18
Hi,
I'm writing from italy and I need your help. I installed Ubuntu 10.4 3 days ago and when I open the firefox page this can't be loaded, even if I war connected whit the ethernet cable. So I follow all the sequence of information after i digit "pppoeconf" in the terminal. At the end the system says that the connection was establieshed, so I restart the computer and when he was loaded again... well...the network manager in the upper-panel near the volume control was disappeared! i create a new wired connection giving him a manual ip, subnet mask and gateway. I tick the option connect automatically, but the computer remain unconnected. Please help me.

Thanks,
Marco

---

### Post by onthatday7yearsago on 2010-05-18
You're going to have to do a little troubleshooting to find more about the problem. First thing to do is check your cables, make sure everything is plugged in. Do you have a router? Or are you directly connected to your modem? Do you have a static IP set up or are you just using DHCP?

Run ifconfig in the terminal and post the results along with whether or not you can ping your default gateway. Also, check to see if you can access the router/modem in firefox by directly inputting the IP address. If you can hit your router but not the internet, then the problem is likely there.

---

### Post by Migaz91 on 2010-05-18
> **onthatday7yearsago said:**
> You're going to have to do a little troubleshooting to find more about the problem. First thing to do is check your cables, make sure everything is plugged in. Do you have a router? Or are you directly connected to your modem? Do you have a static IP set up or are you just using DHCP?

Run ifconfig in the terminal and post the results along with whether or not you can ping your default gateway. Also, check to see if you can access the router/modem in firefox by directly inputting the IP address. If you can hit your router but not the internet, then the problem is likely there.


All the cables are plugged in. I've a router and i'm using the DHCP. After running ipconfig there is the result

**[SIZE=3]eth0[/SIZE]** 
Link Encap:ethernet  HWaddr 00:50:fc:9a:fd:6b
[SIZE=2]inet6 addr: fe80::250:fcff:fe9a:fd6b/64 Scope:link
UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
RX packets:22 errors:4 dropped:0 overruns:0 frame:0
TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:1320 (1.3 Kb) TX bytes:468 (468 b)
interrupt:11 Base addres:0xd000

[B][SIZE=4]lo
[/SIZE][/B][SIZE=4][SIZE=2]Link encap:local loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr:  ::1/128 Scope:Host
UP LOOPBACK RUNNING  MTU:16436  Metric:1
RX packets:8 errors:0 dropped:0 overruns:0 frame:0
TX packets:8 errors:0 dropped:0 overruns:0 carrier:0 collisions:0
txqueuelen:0
RX bytes:480 (480 B) TX bytes (480 B)



after that no i can't find the router in firefox by imputting the IP adress.
[/SIZE][/SIZE][/SIZE]

---

### Post by onthatday7yearsago on 2010-05-18
Looking at the eth0 printout, I don't see an IP address actually being assigned. Not sure if it's never requesting one or if it is being actively denied. Do you have another box handy? I imagine that you're accessing this site with something. If you can connect to the router with that, then I'd check your network settings in Ubuntu to make sure that the card is actually configured for DHCP and doesn't have any random entries in it. 

Also, does anything odd happen when you restart the networking service? It's possible that something is failing at boot time and the error is getting surpressed. I'd also recommend trying to get an update through if at all possible, but I don't see that as a good chance given your connectivity problems.

---

### Post by Migaz91 on 2010-05-18
> **onthatday7yearsago said:**
> Looking at the eth0 printout, I don't see an IP address actually being assigned. Not sure if it's never requesting one or if it is being actively denied. Do you have another box handy? I imagine that you're accessing this site with something. If you can connect to the router with that, then I'd check your network settings in Ubuntu to make sure that the card is actually configured for DHCP and doesn't have any random entries in it. 

Also, does anything odd happen when you restart the networking service? It's possible that something is failing at boot time and the error is getting surpressed. I'd also recommend trying to get an update through if at all possible, but I don't see that as a good chance given your connectivity problems.
 
I have another computer near the first with windows xp and the connection is working of course. Tell me what i've to search in the modem page (is working i checked that). The only odd thing I noticed is that after the guided configuration (after the pppoeconf command in the terminal) the small network icon near the volume control in the upper panel is disappeared and the connection"eth0" listed in network connection under "wired" was disappeared too. Icreated another one bus it doesn't work.

---

