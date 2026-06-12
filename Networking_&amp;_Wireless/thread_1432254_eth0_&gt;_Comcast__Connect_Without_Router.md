---
title: "eth0 &gt; Comcast | Connect Without Router"
date: 2010-03-17
forum: Networking &amp; Wireless
---

### Post by Sensimillia on 2010-03-17
Hello Everyone!  I've been using Ubuntu since 8.04 and I love it, but I think I need a bit of help now.

Normally I have my network setup with a D-Link 514 router and everything works great.  My ISP is Comcast.  When the installer came years ago I had no router and they installed it for a single machine (I was running XP at the time).  My machines are all running Ubuntu Karmic 9.10 64 atm.
In the options of my router it looks like it clones the MAC address of the modem.

The problem is this router is old and constantly drops connections so I have been trying to get a computer running Ubuntu to act as my router for the internal network.  (I do have 2 Network adapters)

When I unhook the router and plug the Internet cable directly from the server to the modem (Motorola) the orange pc activity light does not light up and I have no connection. (I even did a fresh install to see if the installer would set it up, no luck there)
It's not the cable, I can use this cable with the router, and when I plug it directly into my laptop the pc activity light on the router comes on but I can not connect from there either.

My question is: Why am I unable to establish a direct connection to my modem from my server and what steps would I need to take to troubleshoot the problem and resolve the issue?

---

### Post by Iowan on 2010-03-17
Have you tried resetting the modem - sometimes they "lock onto" a MAC and won't service another unless reset.

---

### Post by Sensimillia on 2010-03-17
I have unplugged and plugged the cable modem back in to reset it, but if you mean going into the web user interface and clicking restore factory settings, then no, I have not done that.  I'm not sure what exactly that does and rather not click it other than a last restore.

I don't think it's locked to a mac address cause I can access the modems info @ 192.168.100.1 from my laptop (which I just got) but when I plug it into my server I can not.  I would think that it is a missing driver for the NIC but it work fine with the router set up.

Suggestions?  Does the modem configure itself if I restore factory settings?

---

### Post by Iowan on 2010-03-17
Cycling power (what you did) was what I had in mind for a reset. 
Verify IP address for server - is it in modem's subnet? (**ifconfig -a**)
The "server" is standard CLI-based server - or does it have Desktop and Network Manager installed?

---

### Post by Sensimillia on 2010-03-17
I'm not sure what I'm looking for but here is the output of ifconfig -a
I'm using a fresh install of Karmic Desktop 64 w GNOME for the server at the moment.  I did have Server edition installed with same problem.

Directly Wired to Modem on Boot
```
eth0      Link encap:Ethernet  HWaddr 00:13:d3:e2:[COLOR=Red]##:##[/COLOR]  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:23 Base address:0xe800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:17:3f:ff:[COLOR=Red]##:##[/COLOR]  
          inet6 addr: [COLOR=Red]----::---[/COLOR]:3fff:feff:2637/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr [COLOR=Red]00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00[/COLOR]  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```Router Connected to Modem on Boot
```
eth0      Link encap:Ethernet  HWaddr 00:13:d3:e2:[COLOR=Red]##:##[/COLOR]  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:23 Base address:0xe800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:17:3f:ff:[COLOR=Red]##:##[/COLOR]
          inet addr:192.168.0.103  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: [COLOR=Red]----[/COLOR]::217:3fff:feff:2637/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:132 errors:0 dropped:0 overruns:0 frame:0
          TX packets:149 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:78157 (78.1 KB)  TX bytes:20744 (20.7 KB)

wmaster0  Link encap:UNSPEC  HWaddr [COLOR=Red]00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00[/COLOR]  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

---

### Post by oldfred on 2010-03-17
It looks like you are connecting to your router with wlan not hardwired. Have you not set up eth0? probalby needs DHCP?

Years ago, before my router I tried connecting two different computers and comcast did lock into the HWaddress. After 20 minutes it eventually did connect but I did not want to wait so I spoofed the mac address and that is the hw address I am still using with my router.

---

### Post by oldsoundguy on 2010-03-17
Chirping in on this and a thought:
I had a D-Link 514 and had all kinds of issues with it on Comcast when they upped their speed past the B speed that was the speed of the router.  I switched to a 624 (super g) and have had no issues since.

---

### Post by Sensimillia on 2010-03-17
Yes, I was connecting with my Wireless so I could transfer the terminal output over the network.  Here is the output of ifconfig -a without the wireless adapter connected on boot.

```
eth0      Link encap:Ethernet  HWaddr [COLOR=Red]##:##:##:##:##:## [/COLOR] 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:23 Base address:0x4800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)
```And yes, a new router would easily solve my problem, but that's not as fun as making Ubuntu into a router.

If I can get that computer to connect to Internet directly though the modem I think I'll be good from there.

---

### Post by Iowan on 2010-03-17
Have you configured an IP for eth0 - or is it supposed to get one via DHCP?

---

### Post by Sensimillia on 2010-03-17
It should be getting it's IP via DHCP but since the PC activity light does not come on on the cable modem and I can not connect to the modems' IP, I'm thinking the issue is most likely within the configuration of the NIC.

I really do not want to install Windows as a troubleshooting step, any other suggestions?

(Thanks for the help everyone.)

---

### Post by oldfred on 2010-03-17
Did you test it by plugging into the router? That may tell if wire and port are working. Then you can run some tests.

---

### Post by Sensimillia on 2010-03-17
If I plug it into the router I can connect wired no problem.

I tried changing the mac address of the NIC to the same as the modems' WAN mac, that didn't seem to do anything.

---

### Post by Sensimillia on 2010-03-17
I just noticed that there was one of those square USB ports on the modem and I had a cable.  I unhooked the Ethernet and am using USB now.  As soon as I plugged in the USB cord the pc activity light on the modem came on and Ubunut detected the connection and tried to set it up as eth1, it would not connect until I power cycled the modem and Ubuntu set it up as eth2.

This is not the solution I was hoping for as I still am not sure whats wrong with using the cable but it might be good enough.

I have 2 questions about this set up.

1> Is using USB slower? If so, by how much?
2> Having eth0 and eth2 with no eth1 seem kinda sloppy, how do I fix it? (reboot didn't do it)(Is it reserved for my Ethernet port?) or should I just leave it? 

```
eth0      Link encap:Ethernet  HWaddr 00:13:d3:e2:[COLOR=Red]##:##[/COLOR]  
          inet6 addr: [COLOR=Red]----[/COLOR]::213:d3ff:fee2:9b68/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:48 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:890 (890.0 B)  TX bytes:5871 (5.8 KB)
          Interrupt:23 Base address:0x4800 

eth2      Link encap:Ethernet  HWaddr 00:15:9a:0e:[COLOR=Red]##:## [/COLOR] 
          inet addr:24.10.[COLOR=Red]###.##[/COLOR]  Bcast:[COLOR=Red]##.##.[/COLOR]255.255  Mask:255.255.240.0
          inet6 addr: [COLOR=Red]----[/COLOR]::215:9aff:[COLOR=Red]----[/COLOR]:f82f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7764 errors:0 dropped:0 overruns:0 frame:0
          TX packets:213 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:417604 (417.6 KB)  TX bytes:24881 (24.8 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)
```

---

