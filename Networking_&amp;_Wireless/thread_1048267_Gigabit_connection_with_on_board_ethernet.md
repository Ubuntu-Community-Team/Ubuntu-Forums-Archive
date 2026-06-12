---
title: "Gigabit connection with on board ethernet"
date: 2009-01-23
forum: Networking &amp; Wireless
---

### Post by counterpoint on 2009-01-23
I've just installed a gigabit switch for connection to a gigabit NAS device.  But the LEDs on the switch are indicating that my PC is not connecting at gigabit speed.

The PC is based on an Asus M2NPV-VM motherboard, which is said to include NVIDIA nForce 430 built-in Gigabit MAC with external Marvell PHY.  Operating system is Ubuntu 8.

Is it possible to have the on-board LAN connection run at gigabit speeds?

Or is it necessary to install a network card?  The only gigabit network card that seems to have explicit Linux support from the manufacturer appears to be D-Link.

---

### Post by DFord425 on 2009-01-23
what kind of cable are you using?

---

### Post by counterpoint on 2009-01-23
Belkin Cat 6.

The latest reply from Netgear (getting information about their switch is a real struggle) is that the light will show amber if the connection is half duplex, at whatever speed.

So it would appear I have no way to know, apart from running speed tests, whether data is being transmitted at gigabit speeds.

Is it normal for a PC LAN connection to run half duplex?  Is it possible to run it full duplex, and if it is, does that give any advantage?

---

### Post by sedawk on 2009-01-23
Run
```

# List current settings
sudo ethtool eth0
# are 1000baseT link modes listed?

# at your own risk (if 1000baseT is listed !):
# Re-negotiate speed
sudo ethtool -r eth0
# Force speed manually to gigabit
sudo ethtool -s eth0 speed 1000
# Force full-duplex 
sudo ethtool -s eth0 duplex full

```

There is a change that gigabit lan works but your devices fail
to autonegotiate properly, so they fall back to worst case
settings (100 and half-duplex).
Half-duplex is strange if directly connecting to a switch, half-duplex
was needed in old times when connecting to hubs.

Actually there are many gigabit cards working on Linux, e.g.
check the online configurators for (Linux) servers sold
by IBM or HP and check the network cards you can configure.
There is a good chance they work. E.g. I'm using Intel (e1000 driver)
and Broadcom (tg3 driver(tigon3)) cards.
More important than the vendor is the chipset used on the card!

---

### Post by counterpoint on 2009-01-23
Thanks for that, it's very helpful!  I did not know how to find out what the LAN port was doing.  The result is:
```
	Supported ports: [ MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: MII
	PHYAD: 1
	Transceiver: external
	Auto-negotiation: on
	Supports Wake-on: g
	Wake-on: d
	Link detected: yes

```

which seems to suggest the port is capable of running gigabit full duplex, but is actually running 100 Mbps full duplex.

The result was the same before and after the commands intended to push it to 1000 Mbps.

The chipset is NVIDIA nForce 430.  Is there anything else I can do to persuade the LAN interface to actually run at 1000 Mbps?

---

### Post by marduk667 on 2009-01-23
What does dmesg say?
Please also replug the cable and recheck dmesg

---

### Post by counterpoint on 2009-01-23
Have replugged the ethernet cable at both ends.  Output from dmesg is attached.

---

### Post by sedawk on 2009-01-29
You can try to turn off autonegotiation first:
```

ethtool -s eth0 autoneg off

```
and afterwards try to set 1000 and full duplex and see what
happens.

---

### Post by counterpoint on 2009-01-29
Thanks very much for that.  On its own it didn't seem to make a difference.  But it encouraged me to try again.  Found that setting the speed seemed to be causing an error:
```

martin@martin-development:~$ sudo ethtool -s eth0 speed 1000
Cannot set new settings: Invalid argument not setting speed

```
So tried putting everything in at once, and attempting auto negotiation again:
```

martin@martin-development:~$ sudo ethtool -s eth0 speed 1000 duplex full autoneg on

```
This seemed to work - ethtool states the port is running at 1000 Mbps full duplex, and the switch LED also indicates 1000 Mbps full duplex.  Looks good!

Thanks again for your help.

---

### Post by zzzuppermen on 2009-01-29
Let me share some thoughts.

I had the same problem, with a twist. Plugging in a new Cat6 cable resulted in an orange LED (Fast Ethernet) rather than a green light (Gigabit), but a Cat5e cable popped the green light every time. I only get to work if the cable was really short (like one feet). I returned the cable to the shop and consulted the network specialist. Measuring the cable with a professional cable tester gave some alarming results.

The Certified Cat6 was not 'really' ever a Category 6, because some wires indicated an higher resistance (I think pin 3,4 and 7 in a class "B" wiring) the the others. He also said that it's common for many cabling manufacturing companies to make a copper alloy, rather than pure copper wire. If you're pushing your network for gigabit, you'll probably experience packet dropouts and increased latency. With a regular home use (surfin' the web and sendin' some emails, online games, you name it), it's not a considerably big issue, as you most probably are 'safely' behind the Fast Ethernet's services, since an internet connection faster than 100Mbps sound just too good. But as you're squeezing more data through a bad line, packet losses are going to be proportionally annoying.

Also, the network tester in question costs around 4000 euros (so he sais :P), so you're out of luck.

As for the auto negotiation, it's more like a hardware-to-hardware thing, I noticed. I have 3 computers running Gigabit currently. Restart the machine and stare at the connection indicator LED. The two with a PCI NIC in place (Intel PRO and an Asus with a Sundance chip) indicate Fast Ethernet until the boot process gets to configure the network, and renegotiates it to Gigabit. The third computer (Dell Optiplex) with an on-board NIC gets the green light as you fire it up and has autonegotiated Gigabit speed even at BIOS POST. Instead if you're getting a green light first and than back to orange, than it's a software thing for sure.

In brief, a Cat6 cable that is just a few bucks heavier priced that the good ol' Cat5e will never be Cat6. Another proof that, with the notable exceptions, more $$$ = better product.

My advice is to consult a professional network specialist. If you can find someone with a network cable tester that is capable to certify your connection as Cat6 (or ISO/IEC class D), it only takes 10 minutes to do it and if he's nice, it's free.

Hope this helps.

T.

(Sorry for the long post.)

---

