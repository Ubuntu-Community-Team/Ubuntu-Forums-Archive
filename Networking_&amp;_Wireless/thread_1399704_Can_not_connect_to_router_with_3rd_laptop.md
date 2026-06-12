---
title: "Can not connect to router with 3rd laptop"
date: 2010-02-06
forum: Networking &amp; Wireless
---

### Post by vadarfone on 2010-02-06
Hi

OK, here is the problem;

I have a router with 2 IBM Thinkpads connected.  One Thinkpad is running Ubuntu, and the other is running XP.

They connect to the router with no problems.

I installed Ubuntu on a Sharp Moebius laptop and plugged in the network cable.

NOTHING.

I have tried pinging the laptop; nothing.

I am not sure where the problem is, because my Thinkpads have no problems connecting to the router, with both Ubuntu and XP

I would very much appreciate any help you guys can give me.

Thanks

---

### Post by mushwars on 2010-02-06
if you do 
```
ifconfig
```
does it show that your eth0 is UP and that it has an ip address that was assigned by dhcp? It is very likely that you are not even connected to your router.

---

### Post by vadarfone on 2010-02-06
Thanks for the reply.

Would it be safe to show you my complete ifconfig log?

If so, I will happily show it.

---

### Post by mushwars on 2010-02-06
> **vadarfone said:**
> Thanks for the reply.

Would it be safe to show you my complete ifconfig log?

If so, I will happily show it.

sorry for taking so long to reply, your ifconfig doesnt have any sensitive info in it, it doesnt even have your remote ip address.

All I need to know from it is if you have a local IP address for your computer, you should see somewhere in the eth0 block something like 192.168.0.101 if you do then that is a great sign.

you should then try pinging your router. 

```
ping 192.168.x.1
``` <-- I dont know what your IP is so replace the x with the correct number.

if you can do that then you have a nameserver problem, if not you need to look at your resolv.conf

```
cat /etc/resolv.conf
```

if it is missing the NAMESERVER line than you need to route manually 

```
route add -net default gw 192.168.x.1
```

---

### Post by Iowan on 2010-02-06
You can check **sudo lshw -C network** to verify your interface is recognized. Does the machine get an address via DHCP?

---

### Post by vadarfone on 2010-02-07
> **mushwars said:**
> sorry for taking so long to reply, your ifconfig doesnt have any sensitive info in it, it doesnt even have your remote ip address.

All I need to know from it is if you have a local IP address for your computer, you should see somewhere in the eth0 block something like 192.168.0.101 if you do then that is a great sign.


OK, this is what I get when I run ifconfig

eth0   Link encap:Ethernet HWaddr 00:44:d0:81:fd:a6
         UP BROADCAST MULTICAST MTU:1500  Metric:1
         RX packets: 0 errors:0  dropped:0 overruns:0 frame:0
         TX packets: 17 errors:0  dropped:0 overruns:0 frame:0
         collisions:0 txqueuelen:1000
         RX bytes:0 (0.0B) TX Bytes:0 (0.0B)
         Interrupt:21 Base address:0xe000

eth0:avahi Link encap:Ethernet HWaddr 00:40:d0:81:fd:a6
        inet addr:169.254.10.150 Bcast:169.254.255.255 Mask:255.255.0.0
        UP BROADCAST MULTICAST MTU:1500 Metric:1
        Interrupt:21 Base address:0xe00

lo      Link encap:Local loopback
        inet addr:127.0.0.1 Mask:255.255.0.0
        inet6 addr: ::1/128 Scope:Host
        UP LOOPBACK RUNNING MTU:16436 Metric:1
        RX packets:1939 errors:0 dropped:0 overruns:0 frame:0
        TX packets:1939 errors:0 dropped:0 overruns:0 frames:0
        Collisions:0 txqueuelen:0
        RX bytes:113420 (110.7 KB) TX Bytes:113420 (110.7 KB)

Any ideas?  Thanks a lot for all your help!

Also, I pinged my router and got the following;

From 169.254.10.150 icmp_seq=1 Destination Host Unreachable

---

### Post by vadarfone on 2010-02-07
> **mushwars said:**
> if you can do that then you have a nameserver problem, if not you need to look at your resolv.conf

```
cat /etc/resolv.conf
```

OK, I typed this in and it gave me the following;

nameserver 192.168.0.1

> **mushwars said:**
> if it is missing the NAMESERVER line than you need to route manually 

```
route add -net default gw 192.168.x.1
```

The fact that it gave me the 'nameserver 192.168.0.1' means that I don't have to do this, right?

---

### Post by vadarfone on 2010-02-07
> **Iowan said:**
> You can check **sudo lshw -C network** to verify your interface is recognized. Does the machine get an address via DHCP?

Thanks for helping

OK, when I typed your command in I got this in reply;

*-network
description: Ethernet interface
product: ULi 1689,1573 intergrated ethernet.
vendor: ALi Corperation
physical id: 1b
bus info: pci@0000:00:1b.0
logical name: eth0
version: 50
serial: 00:40:d0:81:fd:a6
capacity: 100MB/s
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list ethernet physical mii 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=uli526x driverversion=0.9.3 latency=128 link=no maxlatency=40 mingnt=20 module=uli526x multicast=yes port=MII

Any ideas?

---

### Post by vadarfone on 2010-02-07
OK, so I have done a bit of digging, and testing, and have the following info which might affect things...

My Router has 4 ports for connecting computers.  I have 3 of these filled now, with my 3 laptops.

I swapped all the cables around to see if it was a router problem, and the 2 Thinkpads connected perfectly on all ports (so that is XP and Ubuntu connecting no problem in every port of the router.

The Sharp Moebius with Ubuntu did not work in any of the ports.

---

### Post by Iowan on 2010-02-07
For whatever reason, either the Sharp isn't receiving a DHCP offer - or it isn't accepting it - the 169.254.10.150 address is an **avahi** address that puts the machine in a subnet of it's own. I presume the DHCP range is bigger than two...

---

### Post by chili555 on 2010-02-07
This may be a hint here:> driver=[COLOR="Red"]uli526x[/COLOR] driverversion=0.9.3 latency=128 [COLOR="Red"]link=no[/COLOR] Please see:  [http://linux.derkeiler.com/Mailing-Lists/Kernel/2008-02/msg00854.html](http://linux.derkeiler.com/Mailing-Lists/Kernel/2008-02/msg00854.html)

I know that's a bit old, but it may be worth investigating. If you cold boot with the cable plugged in, does ifconfig show that eth0 has now gotten a 192.168.x address?

If you do:```
sudo ifconfig eth0 down
```Wait 60 seconds and do:```
sudo ifconfig eth0 up
ifconfig
```Does ifconfig show that eth0 has now gotten a 192.168.x address?

---

### Post by oldfred on 2010-02-07
Why is eth0 showing:
inet addr:169.254.10.150 Bcast:169.254.255.255 Mask:255.255.0.0

if you router is:
nameserver 192.168.0.1

Did you check to see if your settings are identical to the PCs that are working.

---

### Post by vadarfone on 2010-02-07
Thanks for the replys guys.

I will check out all you suggested when I get home from work tonight.

Expect a report in about 10 hours or so.

Cheers!

---

### Post by chili555 on 2010-02-07
> **oldfred said:**
> Why is eth0 showing:
inet addr:169.254.10.150 Bcast:169.254.255.255 Mask:255.255.0.0

if you router is:
nameserver 192.168.0.1

Did you check to see if your settings are identical to the PCs that are working.> the 169.254.10.150 address is an avahi address that puts the machine in a subnet of it's own.This happens when the interface is unable to get an IP address from the router or access point.

---

### Post by vadarfone on 2010-02-08
> **Iowan said:**
> For whatever reason, either the Sharp isn't receiving a DHCP offer - or it isn't accepting it - the 169.254.10.150 address is an **avahi** address that puts the machine in a subnet of it's own. I presume the DHCP range is bigger than two...

OK, I am pretty new to all this, so could you explain to a relative n00b what that means?

I did see that I had an eth0:avahi thing when I type ifconfig -a but I don't know what that means... Sorry for being new to all this!

> **chili555 said:**
> This may be a hint here:Please see:  [http://linux.derkeiler.com/Mailing-Lists/Kernel/2008-02/msg00854.html](http://linux.derkeiler.com/Mailing-Lists/Kernel/2008-02/msg00854.html)

I know that's a bit old, but it may be worth investigating. If you cold boot with the cable plugged in, does ifconfig show that eth0 has now gotten a 192.168.x address?

If you do:```
sudo ifconfig eth0 down
```Wait 60 seconds and do:```
sudo ifconfig eth0 up
ifconfig
```Does ifconfig show that eth0 has now gotten a 192.168.x address?

When I try this, I get 'sudo: unable to resolve host cypher'...

> **oldfred said:**
> Why is eth0 showing:
inet addr:169.254.10.150 Bcast:169.254.255.255 Mask:255.255.0.0

if you router is:
nameserver 192.168.0.1

Did you check to see if your settings are identical to the PCs that are working.

I have no idea.  The settings are not the same as my other working PCs, but I have no idea how to go about changing them, hence I am asking for help here (which, I might add, is VERY much appreciated, thank you.)

> **chili555 said:**
> This happens when the interface is unable to get an IP address from the router or access point.

OK, so is this heading into being an issue with the router do you think?  I mentioned before that I was able to connect to all 4 ports of my router with my 2 working PCs, and everything works fine.

---

### Post by chili555 on 2010-02-08
> When I try this, I get 'sudo: unable to resolve host cypher'...This sounds a bit strange. Please type the commands again:```
sudo ifconfig eth0 down
```Wait 60 seconds.```
sudo ifconfig eth0 up
ifconfig
```Write down exactly what the terminal window returns and post it here. Sorry if it turns out to be lengthy, but we need to do some serious troubleshooting.> OK, so is this heading into being an issue with the router do you think? I think your router is just fine.

---

### Post by Iowan on 2010-02-08
> **vadarfone said:**
> When I try this, I get 'sudo: unable to resolve host cypher'... I don't suppose you recently renamed the host...? That looks like the message that pops up if either */etc/hostname* or */etc/hosts* gets changed without the other.
[http://ubuntuforums.org/showthread.php?t=1391523]("http://ubuntuforums.org/showthread.php?t=1391523")

---

### Post by vadarfone on 2010-02-09
> **chili555 said:**
> This sounds a bit strange. Please type the commands again:```
sudo ifconfig eth0 down
```Wait 60 seconds.```
sudo ifconfig eth0 up
ifconfig
```Write down exactly what the terminal window returns and post it here. Sorry if it turns out to be lengthy, but we need to do some serious troubleshooting.I think your router is just fine.

OK, I looked in etc/hosts and etc/hostname and they were different for some reason.

etc/hosts had it as 'cypher.Workgroup' and etc/hostname had it as 'cypher'

I changed the etc/hosts file to 'cypher', so the two match now.

Did your eth0 Down, then Up, then ifconfig and now get the following...

eth0 Link encap:Ethernet Hwaddr 00:40:d0:81:fd:a6
inet6 addr: fe80:240:d0ff:fe81:fda6/64 Scope:Link
UP BROADCASTING RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:27 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0B) TX bytes:398 (398.0B)
Interrupt:21 Base address:0xe000

lo Link encap: Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16426 Metric:1
RX packets:1614 errors:0 dropped:0 overruns:0 frame:0
TX packets:1614 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:82245 (80.3KB) TX Bytes:82245 (80.3KB)

Different to what I saw before, but still don't know what it all means!

Thanks again for your input, everybody.

We will get to the bottom of this!!

---

### Post by vadarfone on 2010-02-09
Hang on!!!

It's online!!!

YES!!

Turns out it was the fact that the hosts and hostname files were different.  You guys totally rule, thank you SO much!

I will definitely pass this knowledge on to anybody who needs it in the future, thank you.

Superb work.  :D:D

>>Edit...  

Hmm, maybe spoke too soon.  Just rebooted after a big update, and the laptop was not immediately online.

I had to do sudo ifconfig eth0 down, then sudo ifconfig eth0 up.  

The router is showing a connection now, but I can not get online from the laptop itself.  

Also, when I do ifconfig, I don't see the IP anymore...

---

### Post by chili555 on 2010-02-09
What does this tell us about the link?```
sudo ethtool eth0
```Thanks.

---

### Post by vadarfone on 2010-02-10
> **chili555 said:**
> What does this tell us about the link?```
sudo ethtool eth0
```Thanks.

This is what I get...

Settings for eth0:
	Supported ports: [ MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: MII
	PHYAD: 1
	Transceiver: external
	Auto-negotiation: on
	Supports Wake-on: pg
	Wake-on: d
	Link detected: yes

---

### Post by chili555 on 2010-02-10
> Link detected: yesYes! We have made some progress. What is Network Manager doing for us all this time? When you right-click the icon, is networking enabled? If you select Edit Connections and select your wired connection, is Connect Automatically checked?

When you left-click the icon, can you select your wired interface and ask it to connect? What happens?

---

### Post by vadarfone on 2010-02-11
> **chili555 said:**
> Yes! We have made some progress. What is Network Manager doing for us all this time? When you right-click the icon, is networking enabled? If you select Edit Connections and select your wired connection, is Connect Automatically checked?

When you left-click the icon, can you select your wired interface and ask it to connect? What happens?

Hi again!

OK, I can not see the Connect Automatically icon you are referring to; my wired network is set to DHCP if that is what you mean...

To get this machine online, I have to do the sudo ifconfig eth0 down then up thing every time which is not so much of a hassle, but I would ideally like things working automatically...

---

### Post by chili555 on 2010-02-11
Right-click the Network Manager icon and select Edit Connections. Highlight your wired ethernet connection and select Edit. Make sure the Connect Automatically box is checked. See attachments.

If that doesn't do it, we have other methods.

---

### Post by vadarfone on 2010-02-12
I am probably being stupid, but my Network menu looks nothing like that...

Is Network Manager the same as Network in the System / Administration menu?

---

### Post by chili555 on 2010-02-12
> Is Network Manager the same as Network in the System / Administration menu?No. There should be an icon at the upper right that looks like two monitors with an **[COLOR="Red"]X[/COLOR]**.

---

### Post by oldfred on 2010-02-12
It is the same as Network Connections in system, preferences. You have to click on the connection to open the edit button.

---

### Post by vadarfone on 2010-02-13
The only things I have which relate to the network on my system are;

1. System > Administration > Network

2. System > Administration > Network Tools

3. System > Preferences > Network Proxy

4.  The icon on the Panel with 2 monitors.  This is called Network Monitor

None of these things give me the option to Edit my network in the way you suggested.

Is the thing that you are talking about part of 9.10?  I am on 8.04

EDIT> to answer my own question and for any other people reading, YES, the thing Chili555 is referring to is the updated version of the Network Manager.  The options he is asking me to look at are only available in 9.x onwards (I have just upgraded the offending laptop to 9.04 and found the options.

So, Chili555 to answer your original question, when I open the Network Manager (which is called Network Connections on the actual window when it opens), I see nothing.  There is no Wired connection to select!

I am able to get online by doing the Sudo ifconfig eth0 Down then Up thing however...

---

### Post by Iowan on 2010-02-14
> **vadarfone said:**
> 4.  The icon on the Panel with 2 monitors.  This is called Network Monitor.Which version do you run? Gutsy had a different name for (what became) Network Manager. This Hardy box also has a panel icon called Network Monitor that is different than Network Manager (the Configure option doesn't work, either).
Check System>Preferences>Sessions (on Hardy 8.04) to see if Network Manager is checked.

---

### Post by vadarfone on 2010-02-16
Hi

Yeah, it is selected in Sessions.

I am starting to think that this is not an Ubuntu issue; I put the old drive with XP back into the machine to test it out there, and the same problem occured there; the network card took ages to connect to the router, while the other 2 computers I have in the house get connection immediately.

I can get on line with it, but it takes a few minutes to recognize, so maybe the network card is a bit dodgy.

Has anyone ever heard of a dodgy network card taking a while to connect, due to a hardware issue?

---

### Post by vadarfone on 2010-02-26
Morning

Been a while since anybody posted in this thread, but I thought I would update you a little.

I am 99% sure this is an issue with the Network Interface in the machine now.

I have tried XP, Ubuntu, Mint etc with it and the problem remains the same.

The machine is a Japanese version of the base model, bought here in Japan, and the issues I had with Ubuntu also happened with XP and Mint, etc.

The fastest I can get it online is by disconnecting the Network Device, then reconnecting using the Network icon in the Panel.

This gets things running almost immediately.

Nothing I can do will make it go on automatically when the machine comes on, which is very odd, but I will just have to deal with it.

Lessons learned; 

The Ubuntu forum guys are very helpful!
Having a problem is a good thing, as you learn loads when trying to remedy it
Don't by proprietary Japanese stuff.

:)

Thanks for all the help guys.  Great stuff.

---

