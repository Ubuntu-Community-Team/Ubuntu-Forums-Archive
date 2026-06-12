---
title: "No network after resume from sleep"
date: 2010-03-11
forum: Networking &amp; Wireless
---

### Post by SonicSteve on 2010-03-11
Hi guys,

I'm sure this doesn't need a new thread but after searching for a bit I didn't find much about this. The problem is this;

My system sleeps quite well, I can resume from sleep and get back to the desktop. However. the one thing that doesn't resume is > networking.

I can disable> re-enable networking from the NM-applet and it tries again to connect but won't.

I can sudo /etc/init.d/ networking restart, which essentially is the same as above. No connection

I've run ifconfig, and the connection is there but no address. 

Has this bug not been solved? Is it just a driver issue with my particular network card?
It's the realtek 8201, part of the VT8237 chipset.

Does anyone know what to do about this? I've been avoiding sleep mode on this computer for a very long time because of this bug.

---

### Post by koszta on 2010-03-11
Maybe this is just me being stupid but isnt the problem that you are just not getting your ip address ? In that case theoretically running dhclient should help right? I did just a quick cat /etc/init.d/networking|grep "dhc" and it doesnt look like this script triggers the dhclient anyhow...

Dont know if this helps, just my two cents...

Maybe see dmesg and post it here, it might help you too

---

### Post by SonicSteve on 2010-03-11
On one hand yes and on the other no.

True everything seems OK just no DHCP address. 
False because a bug is at fault here.

I'll try the cat command later tonight. Networking restart should fix this also though which I already tried. 

What I'm really looking for is a bug fix not a work around.

---

### Post by koszta on 2010-03-11
Then you wanna do it the hard way then :P I mean I understand and I also usually try to solve my problem but on Linux sometimes solving the problem means avoiding it by a workaround. 
Let me know if I can be of any further help

---

### Post by SonicSteve on 2010-03-11
> **koszta said:**
> Then you wanna do it the hard way then :P I mean I understand and I also usually try to solve my problem but on Linux sometimes solving the problem means avoiding it by a workaround. 
Let me know if I can be of any further help

One thing I'm going to do is try setting the DHCP to Manual IP. Again this isn't a fix but it gives me more information. I'm also about to try the command 2 posts up. On a separate note I'm surprised not more people have this trouble. There are very few threads, and bug reports aren't plentiful either.

---

### Post by SonicSteve on 2010-03-11
Sorry for the double post, I just wanted this post to actually get attention.

I've set the networking to manual IP, tested and connections are good. Put the PC to sleep, and wake up, then no network. I mean nothing, no ping, nothing. 

One difference is that nm-applet at least thinks there is a connection, when it first wakes up nm-applet says not connected, a few seconds later it says connected. However this is a fairly small step forward. Networking is still dead.

If I then restart the PC networking is properly restored. Am I really alone is this problem, or does no one using Ubuntu ever put the computer to sleep?

---

### Post by strider3700 on 2010-05-19
I just wanted to bump this since I have the exact same issue.  If I sleep the PC I have to power the machine down to get the network back again.  a reboot doesn't do it.   When I look at the back of the PC the light on the network card is actually off. power the machine down and then back on and everything is fine again.

lshw provides this info on the nic

```
      description: Ethernet interface
             product: RTL-8139/8139C/8139C+
             vendor: Realtek Semiconductor Co., Ltd.
             physical id: c
             bus info: pci@0000:00:0c.0
             logical name: eth1
             version: 10
             serial: 00:20:18:a0:eb:c3
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.0.102 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
             resources: irq:17 ioport:a000(size=256) memory:fba00000-fba000ff

```

it's an old card,  perhaps it doesn't handle sleep correctly?

---

### Post by strider3700 on 2010-05-19
I was thinking of other things that may be useful to know and ran across ethtool

it's output is
```
Settings for eth1:
	Supported ports: [ TP MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Advertised pause frame use: No
	Advertised auto-negotiation: Yes
	Link partner advertised link modes:  10baseT/Half 10baseT/Full 
	                                     100baseT/Half 100baseT/Full 
	Link partner advertised pause frame use: No
	Link partner advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: MII
	PHYAD: 32
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: pumbg
	Wake-on: d
	Current message level: 0x00000007 (7)
	Link detected: yes

```

---

### Post by jmjohn on 2010-06-27
Same problem here.

---

### Post by HaightsW on 2010-07-04
Try this: [http://ubuntuforums.org/showthread.php?t=1522146&highlight=connection+sleep](http://ubuntuforums.org/showthread.php?t=1522146&highlight=connection+sleep)

---

### Post by Ashimema on 2011-02-11
Anyone know if this ever got fixed?

I have a the same problem as originally described.  Networking will not connect after a system resume (from hibernate or suspend).

Restarting networking as suggested in a number of posts does not fix the problem?

My NIC is on-board my GA-7VT600-P-L motherboard (So is in fact again part of the Via VT8237 chipset! Gigabyte also claim the actaal chip; VT6103L as the Networking controller.)

More Details:

lshw returns;
```

description: Ethernet Interface
product: VT6102 [Rhine-II]
vendor: VIA Technologies, Inc.
physical id: 12
bus info: pci@0000:00:12.0
logical name: eth0
version: 78
serial: 00:0d:61:55:56:28
size: 100MB/s
capacity: 100M/Bs
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=full ip=192.168.1.10 latency=32 link=yes maxlatency=8 mingnt=3 multicast=yes port=MII speed=100MB/s
resources: irq23 ioport:cc00(size=256) memory:e2001000-e20010ff

```

Ubuntu seems to have identified it as VT6102 as opposed to VT6103L?  Also, looks to me that there are new drivers (v5.20) on the VIA site.. but their only relevant for kernels upto 2.6.32 and my system appears to be running 2.6.35-25 so i'm a little hesitant at replacing the drivers?

---

### Post by grahams on 2011-02-12
I just hit this as well after my wife borrow my PC and hibernated it (I usually suspend).

My network card is an old Intel Pro 100 82557.

---

### Post by fuzzywolf on 2011-07-05
i wanna bump this 'cause i have the same simpthoms  eg. no ethernet after suspend to ram (never tried sleep though) moreover the lights on the ethernet socket are both off, when normally at least one is lit even when the cable is unattached. 
To restore ethernet functionality i have to reboot my machine.
Wireless is working fine.

i attach my ethtool output for eth0

```

Settings for eth0:
    Supported ports: [ TP ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Half 1000baseT/Full 
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Half 1000baseT/Full 
    Advertised pause frame use: No
    Advertised auto-negotiation: Yes
    Speed: 100Mb/s
    Duplex: Full
    Port: Twisted Pair
    PHYAD: 0
    Transceiver: internal
    Auto-negotiation: on
    MDI-X: Unknown
    Supports Wake-on: pg
    Wake-on: d
    Current message level: 0x000000ff (255)
    Link detected: no

```hoping it helps

---

### Post by chili555 on 2011-07-05
@fuzzywolf--

Would you please try this and let us have your report? I am wondering if it makes any difference if it's wired or wireless.

[http://ubuntuforums.org/showpost.php?p=11011525&postcount=2](http://ubuntuforums.org/showpost.php?p=11011525&postcount=2)

---

### Post by grahams on 2011-07-28
I can confirm I have the same issue after upgrading to 11.04

---

### Post by chili555 on 2011-07-28
> **grahams said:**
> I can confirm I have the same issue after upgrading to 11.04Did you try the fix I proposed?

---

### Post by Ashimema on 2011-07-29
I gave up and dug another computer out of the bin.

---

