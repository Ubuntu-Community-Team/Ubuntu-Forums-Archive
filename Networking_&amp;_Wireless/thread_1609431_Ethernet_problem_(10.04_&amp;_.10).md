---
title: "Ethernet problem (10.04 &amp; .10)"
date: 2010-10-30
forum: Networking &amp; Wireless
---

### Post by aske on 2010-10-30
Hi,

my machine is a Compaq Prescario cq60 (amd 64bit).

i have a problem with my ethernet card: the connection is very slow. my wireless has no issues.
i cannot browse properly (eg cannot watch youtube videos), my torrent speed is at most 100 whereas with my wireless i got for the same torrent (almost at the same time) 300. (surprisingly, the ping to ubuntu.com is faster (~42ms) than the wireless (~48ms)).
i had this problem in 10.04, and today i upgraded to 10.10 and the problem persists.

on the 9.? installation that i had about a year ago, i did not encounter any problems (also in my windows installation that i had some months ago).

here are some info:
```
anthony@anthony-laptop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: MCP77 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1f:16:d7:2f:b2
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=half latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=10MB/s
       resources: irq:42 memory:c0009000-c0009fff ioport:30f8(size=8) memory:c0007c00-c0007cff memory:c0007800-c000780f

```

and
```
anthony@anthony-laptop:~$ dmesg |grep eth0
[    1.521281] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:1f:16:d7:2f:b2

```

..and
```
anthony@anthony-laptop:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:1f:16:d7:2f:b2  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:40834 errors:3745 dropped:0 overruns:0 frame:1285
          TX packets:34773 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:21407506 (21.4 MB)  TX bytes:12970187 (12.9 MB)
          Interrupt:42 Base address:0x4000 

```

i am not sure if you would need something else.

now, i had this problem for some time, but i was not sure what's the problem since i was always using my wireless. the previous time i tried to fix it, i tried quite some stuff, without any luck:

changed my &#8216;DNS Servers&#8217; to: 208.67.222.222, 208.67.220.220 in the eth0 - ipv4 properties, as well as "ignored" the ipv6.
i also tried the "sudo pppoeconf" command that i found somewhere, but got this error:

```
Sorry, I scanned 2 interfaces, but the Access &#9474; 
&#9474; Concentrator of your provider did not respond. Please &#9474; 
&#9474; check your network and modem cables. Another reason &#9474; 
&#9474; for the scan failure may also be another running pppoe &#9474; 
&#9474; process which controls the modem. 
```

...for which i could not find a solution...

finally i tried this: [http://manpages.ubuntu.com/manpages/lucid/man4/if_nfe.4freebsd.html](http://manpages.ubuntu.com/manpages/lucid/man4/if_nfe.4freebsd.html)
i added this line in the /etc/modules file (that's what it says here [http://www.uluga.ubuntuforums.org/showpost.php?p=9797526&postcount=9](http://www.uluga.ubuntuforums.org/showpost.php?p=9797526&postcount=9)) and restarted; no change (and don't know what to do to check if there was any actual change).


Please give me some ideas of what i should do to fix this issue.
Thank you.

---

### Post by elico on 2010-10-30
may i ask something?
why your eth0 dont have an ip address?

the only difference option that comes in my mind is that you need to config you router properly and make sure that you use the same static ip address  for your Ethernet and your wireless cards.
(you must make sure that you configures properly the port forwarding on your router)
cause if you are connected to the same router with eth and wifi you will get another ip address from the router DHCP server.

good luck
(if you are getting 42 ms while pinging the eth it means that everything is ok from the physical layer and it leaves settings.)

---

### Post by aske on 2010-10-30
> **elico said:**
> may i ask something?
why your eth0 dont have an ip address?

the only difference option that comes in my mind is that you need to config you router properly and make sure that you use the same static ip address  for your Ethernet and your wireless cards.
(you must make sure that you configures properly the port forwarding on your router)
cause if you are connected to the same router with eth and wifi you will get another ip address from the router DHCP server.

good luck
(if you are getting 42 ms while pinging the eth it means that everything is ok from the physical layer and it leaves settings.)

thanx for the reply.
the problem is: i am in a student building where internet is provided by the owners, i do not have a router, only a cable connected to my wall. the wireless that i'm using is NOT mine, it is from the next room - and thus a different address/connection.
i have tried connecting another computer to my cable, and it works fine.

---

### Post by aske on 2010-11-03
Hi, could you please give me any suggestions of what to do, what to check, i cannot use my internet..

thanx..

---

### Post by aske on 2010-11-27
*bump*

still haven't solved my problem,any suggestions?

---

### Post by MooPi on 2010-11-27
Install ethtool to help you change and edit your connection.
```
sudo apt-get ethtool
```
Ethtool has a full range of settings to tweak your adapters. Just check out the man pages after you install. Might help to google the app as well.

---

### Post by aske on 2010-11-27
Thanx very much for the help!

So, i downloaded and got this info: 

```
anthony@anthony-laptop:~$ sudo ethtool eth0
Settings for eth0:
	Supported ports: [ MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Advertised pause frame use: No
	Advertised auto-negotiation: Yes
	Speed: 10Mb/s
	Duplex: Half
	Port: MII
	PHYAD: 1
	Transceiver: external
	Auto-negotiation: on
	Supports Wake-on: g
	Wake-on: g
	Link detected: yes

```

...but i cannot see anything wrong! is there any setting that should be something else for my ethernet to work properly?

---

### Post by MooPi on 2010-11-27
First I would change the speed and the from HalfDuplex to Full. Just possible tweaks.

---

### Post by aske on 2010-11-27
i had tried to change the duplex to full already (and did it again), although i did not think that this could make such a difference.

no luck.

the 10mbps that the speed shows is the actual speed of my network, so i don't know if it would make any difference to change that also. (and when, just to test, i increased it to 100 it broke the connection and had to set the autoneg on to be able to connect :/ )

any other suggestions?
thanx...

---

### Post by MooPi on 2010-11-27
Try different combo Half/100 and see if your NIC can handle it

---

### Post by aske on 2010-11-27
No, unfortunately nothing like this works.
the connection breaks whenever i put a speed higher than 10.
(anyway, why change the speed if it is supposed to be ok?)

thanx, but is there anything else i could check/change? or any idea why this is happening?

---

