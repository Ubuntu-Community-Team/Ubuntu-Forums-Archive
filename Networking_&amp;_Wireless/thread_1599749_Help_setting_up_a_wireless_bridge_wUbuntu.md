---
title: "Help setting up a wireless bridge w/Ubuntu"
date: 2010-10-18
forum: Networking &amp; Wireless
---

### Post by TDShelton on 2010-10-18
Hello all -- first-time caller, long-time listener. These forums have been a great help to me over the months, so thanks for that :)

I have spent the last 24 hours trying to work a wireless bridge (a D-Link DAP-1522) into my network configuration. It would connect to our gateway here at home (some 2WIRE piece of garbage AT&T hands out, but I digress), and two computers (an Ubuntu Desktop and an Ubuntu Server) would connect via the bridge.

The bridge SEEMS to connect to the router, and indeed, the Ubuntu Desktop PC is able to access the internet. The server, however, is not, and neither computer can communicate with the other (ping, SSH, etc.) furthermore, the router recognizes the presence of these two computers on some level, but does not seem to know their IP addresses (I assume this is related to the computers' inability to communicate).

Before I get too far into this, here are a few links/items for the sake of clarity. The first is a shoddy diagram of my (proposed) network topology, for all of you out there who, like myself, understand things visually:
[LIST]
[*][http://dl.dropbox.com/u/2345835/network/topology.png](http://dl.dropbox.com/u/2345835/network/topology.png)
[/LIST]

This is the output from running "ifconfig eth0" on the Ubuntu Desktop PC, which sits behind the bridge. The PC is connected, and can ping hosts across the Internet, but can only ping the router locally (that is, it can't ping any other device in the house, on either side of the bridge):

```
eth0      Link encap:Ethernet  HWaddr 00:1c:c0:2a:53:f6  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:c0ff:fe2a:53f6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:323829 errors:0 dropped:0 overruns:0 frame:0
          TX packets:202626 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:364906991 (364.9 MB)  TX bytes:20934424 (20.9 MB)
          Interrupt:20 Memory:e3500000-e3520000 
```

The router uses wireless encryption, not MAC addresses, to restrict access/traffic, and all wireless devices (including the bridge) have been provided with the proper credentials. There shouldn't be any devices being denied access on account of their MAC address. In fact, the router's control panel lists the PC and the Server among the recognized devices (even lists their MAC addresses), but provides no IP address and always considers the two computers to be "offline." And yet, I am writing this very post from the Ubuntu PC. Sigh.

I am very comfortable with computers, and reasonably comfortable with Ubuntu/Linux and the Linux command line -- I've been using the operating system for just over a year now -- but networking issues have always been perched right on the edge of my understanding. In short, it's likely this issue has more to do with me than it does with the hardware itself (although the more forums I browse, the more I start to doubt this bridge...).  Any assistance in sleuthing/solving this problem would be greatly appreciated!

---

### Post by HouTex on 2011-02-05
FWIW, I have a D-Link 1522 and I might have a similar problem.  Mine is set up in AP mode (not Auto or Bridge mode) by the switch on the side of the 1522.  I have another WAP in my home (a Linksys) and it works fine.  The Linksys uses WEP encryption.  The 1522 is set to WPA encryption because my Blue Ray DVD in that room will not work with WEP.  The Linkysis connects automatically to my system (a Dell L13, Ubuntu 9.1, Broadcom 4312 wireless card, STA driver) and it works very well.  But the 1522 is not recognized through Network Manager even though it is NOT set up as a hidden network.  I can access it by connecting to a new wireless network and it says I'm connected, but Firefox will not connect to the internet and I can't ping anything.  One problem might be that when I go to system/admin/network connections (the 1522 DOES show up there) it says that it's set up as an ad hoc network.  I try changing to infrastructure but it does not seem to take it--when I save it and then return it still says ad hoc.
 
I've tried everying in the sticky thread on Broadcom 43XX issues and nothing has allowed me to use the 1522 wirelessly.  I've also disabled encyption on the 1522 and it still won't connect to the internet.  My work around is to plug an ethernet cable to the back of the 1522 and it works fine.  Luckily, it has female connectors and having to use a wired connection in that room isn't a huge inconvenience.

---

### Post by TDShelton on 2011-02-05
Thanks for the input, HouTex. For myself, I wound up returning the bridge and just running an Ethernet cable for the server. A long cable across rooms is inelegant and exactly what I was trying to avoid, but at least it worked from day 1.

---

