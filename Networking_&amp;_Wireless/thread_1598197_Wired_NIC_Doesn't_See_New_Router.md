---
title: "Wired NIC Doesn't See New Router"
date: 2010-10-16
forum: Networking &amp; Wireless
---

### Post by fullmoonguru on 2010-10-16
Switch actually.  I bought a switch, connected it to our router, and moved the patch cords to the switch.  All but one of the workstations connect & work fine.  If I plug the non-connecting wire into my laptop it connects.  If I plug the non-connecting wire back into the router, the workstation connects.

So...it seems that this particular workstation will only see the address of the old router.  It's stuck in there & won't refresh.  Two of the PC's & the laptop are running 10.04 (Mint 9 Actually), and one has Windows XP on it.  The problem is with one of the 3 10.04 boxes.  

I have tried removing the power cord & MB battery and leaving them out over night.  Also cleared the bios.  Same results.  Connects fine to the old router but will not connect to the new switch.

---

### Post by Iowan on 2010-10-16
I presume you've tried swapping cables between the non-working machine and a working machine (ie. you tried the non-working in a different port)?

---

### Post by fullmoonguru on 2010-10-16
I tried removing the patch cable from the PC & connecting it to a laptop & it works.  I also tried switching ports at the switch & another worksation works in the same port.

  	 	 	 	p { margin-bottom: 0.08in; }  Results of ifconfig:
 

```
ifconfig eth2  
 eth2      Link encap:Ethernet  HWaddr 00:01:2e:23:a7:d5   
           UP BROADCAST MULTICAST  MTU:1500  Metric:1  
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)  
           Interrupt:21 Base address:0xe000

```

 If I ping one of my local ip addresses, I get no change in the window. 0 everything.  No indication that I even tried.  If I ping ubuntu.com it says the address cannot be found.

---

### Post by Iowan on 2010-10-16
eth2? What are results of **ifconfig -a** ?

---

### Post by fullmoonguru on 2010-10-16
ifconfig -a 
eth2      Link encap:Ethernet  HWaddr 00:01:2e:23:a7:d5  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:21 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:172 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:172 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:13760 (13.7 KB)  TX bytes:13760 (13.7 KB) 

vboxnet0  Link encap:Ethernet  HWaddr 0a:00:27:00:00:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 

wlan0     Link encap:Ethernet  HWaddr 00:25:d3:ef:ac:69  
          BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by fullmoonguru on 2010-10-19
Bump

---

### Post by Iowan on 2010-10-19
Curious what happened to eth0 (and eth1?). The vboxnet0 is also curious - virtualization?

---

### Post by fullmoonguru on 2010-10-20
So am I.  I don't remember doing anything strange when setting it up, but it's certainly possible.  I switched our network over to Linux so I have plenty swirling around in my head.

I have a VB with XP in it but the problem I'm having is with the host.

Again, I can move the wire from the new switch back to the router & it works fine.  So it's not like we have a problem with the machine per se, it seems that it's just holding on to the MAC address of the router or something.

---

### Post by relay_man on 2010-10-21
1) When you plug the cable from the the workstation into the switch, does the link light on the switch illuminate?

2) Is the cable between the workstation and switch a straight through, or crossover?

Connecting workstation to switch,  or workstation to router normally requires a straight cable.  Routers are typically somewhat more sophisticated than switches and usually can detect a crossover cable.  
The router will perform autocrossover and things will work fine.
Switches for home use are often more simple and not capable of detecting a crossover cable.

---

### Post by fullmoonguru on 2010-10-23
They're just regular patch cables.  As I posted above, I can remove the cable from the workstation and insert it in my laptop & it makes the wired connection so it's not the cables.  I then put it back in the workstation - no connection.  Then I can go move the other end of the cable from the switch to the router & the workstation connects.  Both the laptop & workstation are running Ubuntu 10.04 (Mint 9).

There is no light on the switch when it's not working.

---

### Post by relay_man on 2010-10-23
Perhaps I should go about this a different way.

Assuming the switch has link lights that you can observe,
plug the cable from the workstation into the switch.  Does
the link light illuminate shortly after you connect the cable?

---

### Post by fullmoonguru on 2010-10-24
The switch does have lights.  I get no light when plugging this cord in.

---

### Post by fullmoonguru on 2010-10-30
Still trying to figure this one out.

---

### Post by elico on 2010-10-30
what is the brand of the switch?
i have edimax br-6204WG router that if you connect my specific REALTEK GB Ethernet card (O.B) the router
(used as switch and AP) will go berserk starts restarting itself just from nowhere.

so what i did was connecting the computer to another switch and wiring from the switch to the router.

---

### Post by SeijiSensei on 2010-10-31
What are the contents of /etc/network/interfaces?  If there's an "eth2" stanza, try renaming eth2 to eth0.  

Disable the wifi adapter and shutdown any virtual hosts. What does ifconfig show when you reboot?

---

### Post by relay_man on 2010-10-31
Sorry for the delay.

Okay, obviously you aren't willing to give up on this yet, so I'm not going to give up either...

I asked:

> Assuming the switch has link lights that you can observe,
plug the cable from the workstation into the switch. Does
the link light illuminate shortly after you connect the cable?

Your response:

> The switch does have lights. I get no light when plugging this cord in. 


So, let's stop right there and review some facts.

When physical connections are made between hosts and switches/routers and everything is proper, you will get a link light showing the devices are recognized. (connected if you will)  at the layer 2 level. (mac or physical address level)

You've said previously that:

1) You've tried connecting the offending Ubuntu host to different ports on the switch, but no connection occurred.

2) Connecting the Ubuntu host directly to a port on the router is
successful and the connection is made.  

So, the cable isn't defective, but there must be something different about the ports on the switch when compared to the ports on the router.
 
It is very common for switches to be more simple (and less expensive) and many cannot recognize crossover cable. (no link light)

Most routers ARE more complex, and can re-configure their ports when necessary to utilize a crossover cable when one is connected.
(Even though a straight cable is the correct cable to use)

In your case, I may be completely wrong and if so I've made a complete *** of myself in front of the world.  So be it. I'm getting used to it.:(

But based on the posts so far, I don't think you've checked the cable to see whether it is indeed a straight or crossover cable.
Nor have you checked the documentation that came with your switch to see whether it can do "auto-crossover".

So, at present I'm sticking with my guess that you have a crossover cable and the switch cannot work with it.

Earlier you said:

> They're just regular patch cables. 

No, they aren't.  There is no such thing.

You need to know for sure which type of cable you have if this problem is to be solved.

It is easy to check a cable to see if it is configured as straight, or crossover. (There is also a third configuration called rollover, but if you've got one of those...)
  Hold both ends up in front of you with the locking tab oriented away from your face.  CAREFULLY observe the wiring inside of the plastic plug on both.  You may have to use a magnifying glass to make sure.
What you are checking is that the colored wires (in sequence from left to right) are the same.  If they are, your cable is configured "straight".

If the colored wires are not in the same order on both plugs, you've a crossover cable and you REALLY need to use a straight cable for a host-to-switch connection.

As hard as it may be to believe, I AM trying to help.

---

### Post by fullmoonguru on 2010-11-03
Thank you for the responses!

The switch & router are both D-Link.  The switch recognizes straight through or crossover cables.  The important thing to remember in the diagnostics here, is that I can remove the cable from the box, plug it into a laptop, & get a connection.  That tells me it has to be the computer.

Contents of etc/network/interfaces:

```
auto lo
iface lo inet loopback
```

So I just ran ifconfig for the hell of it & noticed that it now lists "eth 0" instead of "eth2":

  	 	 	 	p { margin-bottom: 0.08in; }```
ifconfig  
 eth0      Link encap:Ethernet  HWaddr 00:01:2e:23:a7:d5   
           inet addr:192.168.0.197  Bcast:192.168.0.255  Mask:255.255.255.0  
           inet6 addr: fe80::201:2eff:fe23:a7d5/64 Scope:Link  
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1  
           RX packets:955 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:1072 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  
           RX bytes:160553 (160.5 KB)  TX bytes:118544 (118.5 KB)  
           Interrupt:21 Base address:0xc000  
 

 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0  
           inet6 addr: ::1/128 Scope:Host  
           UP LOOPBACK RUNNING  MTU:16436  Metric:1  
           RX packets:247 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:247 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:0  
           RX bytes:18980 (18.9 KB)  TX bytes:18980 (18.9 KB)  
 

 wlan0     Link encap:Ethernet  HWaddr 00:25:d3:ef:ac:69   
           UP BROADCAST MULTICAST  MTU:1500  Metric:1  
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)  

```

So I moved the cable to the switch & it now works.  Not sure how eth0 got to eth2, or how it got back.

---

### Post by relay_man on 2010-11-05
Whew!!!!!

Well, I'm not sure either.  I move my wired connection around to several other boxes routinely and I've never experienced the connection being renamed.
Do you have several connections available in network manager?  Auto eth0, eth1, etc.?

Solved?

---

### Post by fullmoonguru on 2010-11-24
It was solved but now I switched the mb to another machine & I have no connection again.  Moving the cable to the router doesn't change it though, and there is now a light on the switch.  Not sure if this is just an unrelated problem so I started a new thread.[URL="http://ubuntuforums.org/newthread.php?do=postthread&f=336"]
[/URL]

---

