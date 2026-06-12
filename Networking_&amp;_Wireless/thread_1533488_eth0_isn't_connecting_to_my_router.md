---
title: "eth0 isn't connecting to my router"
date: 2010-07-18
forum: Networking &amp; Wireless
---

### Post by ahungryhobo on 2010-07-18
I downloaded wubi, installed ubuntu, and booted it up. Everything went smooth, it finished installing with no problems. It restarts again and I login. Firefox opens.....server not found.

That brings you to where I am now. It says that eth0 is connect. I manually changed the ip address, the netmask and gateway. Still I have no luck.

route reads as follows:
Kernel IP routing table
Destination          Gateway                 Genmask                          Flags   Metric     Ref      Use Iface
192.168.1.1         *                                 255.255.255.255       UH      0                 0            0     eth0
10.0.0.0                 *                   255.255.255.255    U           1                  0            0     eth0
link-local              *                                 255.255.0.0                   U            1000       0            0     eth0 
default           192.168.1.1        0.0.0.0                              UG         0                  0           0      eth0
If you need any more information, just as and I will get it as soon as possible.
Any help would be greatlyyyyyy appreciated.

---

### Post by Sanjeevtrip on 2010-07-18
I dont think you are connecting to the gateway.
If you have 192.168.1.1 it should be private network, are you using any router/modem or is there any proxy server?

---

### Post by ahungryhobo on 2010-07-19
I'm using 2 routers actually. I think that's what is screwing me up.
192.168.1.1 is the router that connects to my modem like device. 192.168.1.9 is the one that connects the the previously mentioned router. Although I'm not quite sure if that is the right IP for the second router...
Also, my devices all started getting assigned IP's that are like; 10.0.0.3 Before they were being assigned; 192.168.1.3 and so on. But that was before I installed ubuntu.

---

### Post by ahungryhobo on 2010-07-19
I fixed it!!!
The internet is a little slow though...not sure why that is. I guess I'll try tweaking with it a little more when I feel like it.
All I did was go to the network manager and edit eth0;
Address------Netmask----------Gateway
10.0.0.11     255.255.255.0    10.0.0.1
10.0.0.11     255.255.255.0    192.168.1.1
10.0.0.11     255.255.255.0    192.168.1.9

Then in the DNS server I put: 10.0.0.1, 192.168.1.1, 192.168.1.9

Just so you know, 10.0.0.1 is the LAN IP on my first router, and 192.168.1.9 is the internet IP on the first router. I wasn't sure which would work, so I tried both.
And 192.168.1.1 is the second router which hooks up to the modem.

Hopefully this will help anyone that has the same problem as me!

---

