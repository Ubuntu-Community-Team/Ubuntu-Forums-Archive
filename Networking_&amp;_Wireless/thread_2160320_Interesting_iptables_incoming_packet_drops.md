---
title: "Interesting iptables incoming packet drops"
date: 2013-07-06
forum: Networking &amp; Wireless
---

### Post by Azrael84 on 2013-07-06
Hi,  I've attached my iptables rules script as a .txt attachment for reference, but they are fairly standard rules that I've patched together from various online sources. Things seem to be working pretty well, but I am confused about some of the log entries in `/var/log/kern.log'. I'm not quite sure what these incoming connections are, or ineed, why they are being dropped. As an example:  ```
 Jul  6 16:18:29 mylappy kernel: [29424.535475] IPTables IN Packet Dropped: IN=eth1 OUT= MAC=c4:17:fe:65:51:f8:00:26:44:59:a6:10:08:00 SRC=67.215.67.15 DST=192.168.1.79 LEN=52 TOS=0x00 PREC=0x00 TTL=57 ID=4134 DF PROTO=TCP SPT=80 DPT=48812 WINDOW=8326 RES=0x00 ACK RST URGP=0  
```  Similarly other websites with SPT=80 that continually crop up: (showing SRC,DST,PROTO, SPT,DPT only) ```
     
SRC=67.215.67.31 DST=192.168.1.79 PROTO=TCP SPT=80 DPT=55202   ( OPENDNS-NET-3)    
SRC=173.194.34.183 DST=192.168.1.79 PROTO=TCP SPT=80 DPT=40869 (GOOGLE)     
SRC=173.194.34.191 DST=192.168.1.79  PROTO=TCP SPT=80 DPT=50716 (GOOGLE)    
SRC=74.125.136.16 DST=192.168.1.79  PROTO=TCP SPT=993 DPT=57026  (Google Inc) 993 is #GMAIL IMAP SSL, which I have allowed outboad...but surely conntrack should be allowing the inbound?    
SRC=192.168.1.254 DST=192.168.1.79 PROTO=TCP SPT=80 DPT=43065  (ROUTER)    
SRC=31.13.72.33 DST=192.168.1.79  PROTO=TCP SPT=443 DPT=59306 (??)    
SRC=78.129.223.36 DST=192.168.1.79  PROTO=TCP SPT=80 DPT=37455  (Iomart Hosting Ltd)    
SRC=69.171.248.16 DST=192.168.1.79  PROTO=TCP SPT=443 DPT=51225 ( Facebook, Inc.)    
SRC=23.48.157.195 DST=192.168.1.79 PROTO=TCP SPT=443 DPT=58934 (AKAMAI)    
SRC=213.248.117.9 DST=192.168.1.79  PROTO=TCP SPT=443 DPT=38040 ( Akamai International B.V.)    
SRC=46.33.76.9 DST=192.168.1.79  PROTO=TCP SPT=443 DPT=38443  (AKAMAI-TINET)    
SRC=206.19.49.183 DST=192.168.1.79  PROTO=TCP SPT=80 DPT=55513  (CERFnet CERFNET-BLK-206 )    
SRC=190.93.246.58 DST=192.168.1.79  PROTO=TCP SPT=80 DPT=52007 (CloudFlare ?? http://en.wikipedia.org/wiki/CloudFlare)    
SRC=54.230.9.150 DST=192.168.1.79 PROTO=TCP SPT=80 DPT=58305 (Amazon Technologies Inc) 
```  Yet, I get no visible problems accessing these websites.  1)  Why are these websites connecting to me at all?   (I gather SPT=80, DRT=55202 means they are trying to connect to me on 55202 and the packet originated out of the servers port 80?)  1b)  If the connections are related to my established outgoing connections to them, why aren't my conntrack rules letting them through?  2)  Should I make a rule to allow such connections?  2b) If so, Would adding a rule like           iptables -A INPUT -i eth0 -p tcp --dport 80 -m state --state NEW,ESTABLISHED -j ACCEPT           iptables -A OUTPUT -o eth0 -p tcp --sport 80 -m state --state ESTABLISHED -j ACCEPT            iptables -A INPUT -i eth0 -p tcp --dport 443 -m state --state NEW,ESTABLISHED -j ACCEPT           iptables -A OUTPUT -o eth0 -p tcp --sport 443 -m state --state ESTABLISHED -j ACCEPT  help, or is this really to allow me to function as a webserver and host documents on 80? Therefore not what I need...  Sorry about the long post, any help would be greatly appreciated  Thanks.

---

### Post by Azrael84 on 2013-07-06
PS. Sorry, I don't seem to be able to get line breaks in the above for some reason, so it looks quite messy....

---

### Post by The Cog on 2013-07-06
I took the liberty of adding newlines to your list.

Your rules look OK to me apart from this line which I don't think is needed, you already have a rule to allow in established connections.
```
iptables -A INPUT   -p tcp --sport 22 -m state --state ESTABLISHED -j ACCEPT
```

I can't tell about all the other log entries you list because you cut off the important stuff, but the first entry contains the flags "ACK RST". The Ack means this acknowledges another packet in the connection, and RST means that it is a Reset request - close the connection forcibly. My guess is that in this case, it is a response to a connection request that didn't come from your machine (another machine sending packets claiming to be from your source address). I don't think you should allow these in, and neither do I think they are cause for concern. There is a low-level babble of odd packets all over the internet, and I think this is just another oddity. Unless it's happening a lot, ignore it.

---

### Post by Azrael84 on 2013-07-06
> **The Cog said:**
> I took the liberty of adding newlines to your list. 

Thanks very much for the reply and edits. I'm not sure why it wasn't registering the newlines I put in in the edit box.

> **The Cog said:**
> 
Your rules look OK to me apart from this line which I don't think is needed, you already have a rule to allow in established connections.
```
iptables -A INPUT   -p tcp --sport 22 -m state --state ESTABLISHED -j ACCEPT
``` 

OK, I will get shut of that.

> **The Cog said:**
> 
I can't tell about all the other log entries you list because you cut off the important stuff, but the first entry contains the flags "ACK RST". The Ack means this acknowledges another packet in the connection, and RST means that it is a Reset request - close the connection forcibly. My guess is that in this case, it is a response to a connection request that didn't come from your machine (another machine sending packets claiming to be from your source address). I don't think you should allow these in, and neither do I think they are cause for concern. There is a low-level babble of odd packets all over the internet, and I think this is just another oddity. Unless it's happening a lot, ignore it.

It is happening a lot actually (maybe 20 of these lines every 10mins!), reems of the stuff in my logs each day, which is quite annoying as it makes reading the logs pretty difficult. If it acknowledges another packet in connection shouldn't the conntrack allow it?  Out of curiosity why would these machines be sending packets claiming to be from my source?


 I can give you a few more full samples if it helps:

```

Jun 30 12:53:45 mylappy kernel: [70591.941929] IPTables IN Packet Dropped: IN=eth1 OUT= MAC=c4:17:fe:65:51:f8:00:26:44:59:a6:10:08:00 SRC=67.215.67.31 DST=192.168.1.79 LEN=40 TOS=0x00 PREC=0x00 TTL=57 ID=41849 DF PROTO=TCP SPT=80 DPT=37990 WINDOW=0 RES=0x00 RST URGP=0 

```

```

Jul  1 22:52:14 mylappy kernel: [41083.903958] IPTables IN Packet Dropped: IN=eth1 OUT= MAC=c4:17:fe:65:51:f8:00:26:44:59:a6:10:08:00 SRC=69.171.248.16 DST=192.168.1.79 LEN=459 TOS=0x00 PREC=0x00 TTL=83 ID=28636 DF PROTO=TCP SPT=443 DPT=53439 WINDOW=133 RES=0x00 ACK PSH URGP=0 

```

```

Jul  1 23:53:34 mylappy kernel: [44756.875765] IPTables IN Packet Dropped: IN=eth1 OUT= MAC=c4:17:fe:65:51:f8:00:26:44:59:a6:10:08:00 SRC=54.230.11.189 DST=192.168.1.79 LEN=60 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=TCP SPT=80 DPT=60534 WINDOW=5792 RES=0x00 ACK SYN URGP=0 

```


Most do seem to be "ACK" followed by something: "ACK SYN/FIN/RST/PSH" whilst others are just "RST"..

I also seem to be getting a few internal packets dropped such as

```

Jul  2 21:04:34 mylappy kernel: [44065.814623] IPTables IN Packet Dropped: IN=eth1 OUT= MAC=01:00:5e:7f:ff:fa:00:26:44:59:a6:10:08:00 SRC=192.168.1.254 DST=239.255.255.250 LEN=319 TOS=0x00 PREC=0x00 TTL=1 ID=55568 PROTO=UDP SPT=8944 DPT=1900 LEN=299

Jun 30 12:19:16 mylappy kernel: [68526.754945] IPTables IN Packet Dropped: IN=eth1 OUT= MAC= SRC=192.168.1.79 DST=192.168.1.255 LEN=72 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=57621 DPT=57621 LEN=52 

 
```

Is there a line a should be adding to iptables to make sure these get through? whatever they are...

---

### Post by The Cog on 2013-07-07
There are a couple more RST packets, and a couple of packets that look as though they belong to existing connections. But if You don't know what they are for, and don't have any operational problems while they are being blocked, then I see no need to allow them in. 

Reading firewall drop logs will keep you awake at night.

---

### Post by Azrael84 on 2013-07-07
You are right about how you can spend to long thinking about these things but last question!

```
[22725.503207] netfilter:in dropped: IN=eth1 OUT= MAC= SRC=192.168.1.79 DST=192.168.1.255 LEN=72 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=57621 DPT=57621 LEN=52 
```

```
 netfilter:in dropped: IN=eth1 OUT= MAC= SRC=192.168.1.79 DST=239.255.255.250 LEN=129 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=50877 DPT=1900 LEN=109 
```

What can this possibly mean? 192.168.1.79 is my IP on the local network, so how can I receive an incoming packet from myself?? I gather 192.168.1.255 is broadcast, but what is going on here?

---

### Post by Azrael84 on 2013-07-07
I've since found out that "SRC=192.168.1.79 DST=192.168.1.255" is actually spotify broadcasting its existent across the network trying to find other computers with spotify on the network....I'm still slightly confused as to why it appears with my IP as SRC yet is an incoming packet.....Is it that I also receive the broadcast packet like everyone else on the network, even thought I was the original sender?  I'm still confused about the latter log entry, and also what I should be doing in general regarding internal local traffic, so as to not open myself to packet spoofs/bogus packets, yet allow genuine local traffic...

---

### Post by Azrael84 on 2013-07-07
I've since found out that "SRC=192.168.1.79 DST=192.168.1.255" is actually spotify broadcasting its existent across the network trying to find other computers with spotify on the network....I'm still slightly confused as to why it appears with my IP as SRC yet is an incoming packet.....Is it that I also receive the broadcast packet like everyone else on the network, even thought I was the original sender?  I'm still confused about the latter log entry, and also what I should be doing in general regarding internal local traffic, so as to not open myself to packet spoofs/bogus packets, yet allow genuine local traffic...

---

### Post by The Cog on 2013-07-07
DST=192.168.1.255 is a local LAN broadcast. If it's spotify, then I guess it is trying to advertise its presence to any other spotify instances on the same (your) LAN. Although I don't understand why it says "in". 

It seems to be arriving on eth1. Is eth0 active at all? Could eth1 be wireless? I'm windering if your own transmissions on eth0 could be finding your way back round and into eth1. Just a thought.Some time spent with tcpdump could confirm.

SRC=192.168.1.79 DST=239.255.255.250 would appear to be your machine transmitting UPnP packets. I found this: [http://www.nthelp.com/upnpscrewup.htm](http://www.nthelp.com/upnpscrewup.htm) Again, strange that it looks like it's incoming. 

Maybe there's another computer on the same LAN with the same IP address?

---

### Post by Azrael84 on 2013-07-07
> **The Cog said:**
> DST=192.168.1.255 is a local LAN broadcast. If it's spotify, then I guess it is trying to advertise its presence to any other spotify instances on the same (your) LAN. Although I don't understand why it says "in".  

  What I gathered from google was that spotify is looking for other clients on the network, so broadcasts then listens on 57621, and because the packet is "broadcast" everyone on the network including myself gets it? (even though I sent it) ("no MAC address involved in packets..." means it's the local IP stack not the switch/router which would never rebroadcast to original sender......as you can tell my understanding of these things is vague, but perhaps that will make sense to you.)

  >  It seems to be arriving on eth1. Is eth0 active at all? Could eth1 be wireless? I'm windering if your own transmissions on eth0 could be finding your way back round and into eth1. Just a thought.Some time spent with tcpdump could confirm.   

eth1 is my wireless yes. eth0 is just my laptop's wired network card (which I never use, so is inactive):

```
 eth0      Link encap:Ethernet  HWaddr 00:26:b9:23:ce:df             UP BROADCAST MULTICAST  MTU:1500  Metric:1           RX packets:0 errors:0 dropped:0 overruns:0 frame:0           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0           collisions:0 txqueuelen:1000            RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)           Interrupt:41 Base address:0xc000  
```  ```
  lshw -C network  *-network                       description: Wireless interface        product: BCM4312 802.11b/g LP-PHY        vendor: Broadcom Corporation        physical id: 0        bus info: pci@0000:03:00.0        logical name: eth1        version: 01        serial: c4:17:fe:65:51:f8        width: 64 bits        clock: 33MHz        capabilities: bus_master cap_list ethernet physical wireless        configuration: broadcast=yes driver=wl0 driverversion=6.20.155.1 (r326264) ip=192.168.1.79 latency=0 multicast=yes wireless=IEEE 802.11abg        resources: irq:17 memory:f0400000-f0403fff   *-network        description: Ethernet interface        product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller        vendor: Realtek Semiconductor Co., Ltd.        physical id: 0        bus info: pci@0000:04:00.0        logical name: eth0        version: 02        serial: 00:26:b9:23:ce:df        size: 10Mbit/s        capacity: 100Mbit/s        width: 64 bits        clock: 33MHz        capabilities: bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
```

  *But then looking at the logged packets from iptables the SRC MAC seems to match the MAC of eth0??? 00:26:b9:23:ce:df ***(EDIT: this is just wrong the source MAC in the packets is actually 00:26:44:59:a6:10 which is the router MAC as expected; I obviously only read the first two blocks!)**

   >  SRC=192.168.1.79 DST=239.255.255.250 would appear to be your machine transmitting UPnP packets. I found this: [http://www.nthelp.com/upnpscrewup.htm](http://www.nthelp.com/upnpscrewup.htm) Again, strange that it looks like it's incoming.    thanks  > Maybe there's another computer on the same LAN with the same IP address?  

No other computers.

Yes, think you're right about the UPnP packets.....I think the key piece of information in the packet is "MAC= SRC=192.168.1.79 DST=239.255.255.250" again the DST is multicast and the MAC is empty, so I think this is a situation very similar to the broadcast packet above......I sent it out, but because it's multicast it also comes back to me (through local IP stack or some such (MAC less)??).

---

### Post by The Cog on 2013-07-08
> What I gathered from google was that spotify is looking for other clients on the network, so broadcasts then listens on 57621, and because the packet is "broadcast" everyone on the network including myself gets it? (even though I sent it) ("no MAC address involved in packets..." means it's the local IP stack not the switch/router which would never rebroadcast to original sender......as you can tell my understanding of these things is vague, but perhaps that will make sense to you.)
That possibility had not occurred to me, but it makes perfect sense. I think I will assume that you are right.

---

