---
title: "How to set up a WiFi Sub-Net"
date: 2009-09-21
forum: Networking &amp; Wireless
---

### Post by misterfixit on 2009-09-21
I have a successful network in my house.  Cable into a wired adaptor and then cables to each computer. I have an Amateur Radio "Shack" located in my workshop building about 50 feet away.  Would someone be kind enough to lead me by the hand in setting up a wireless network inside the "Shack", using a WiFi adaptor attached to the Wired Adaptor in the house?  I have so far set all the hardware into place and the 3 computers in teh Shack an see the WiFi output from the DLINK device in my house. I want to build a sub net in the Shack using those three WiFi computers and have them fed by the WiFi adaptor which is plugged into the Wired Adaptor in the house.  At least I think this is how I should do it.

Here is what it looks like so far:

House:

Wired Router attached to Comcast Cable
PC #1 = 192.168.0.100
PC #2 = 192.168.0.111
PC #3 = 192.168.0.112
HP Laserjet 4000N = 192.168.0.113
HP Scanner/Printer/Fax = 192.168.0.114
Wireless Router = ???.???.?.???

Shack:

PC #1 with WiFi card = ???.???.?.???

Many thanks in advance for your help.

Dave

Wireless Router

PC #1 =

---

### Post by capscrew on 2009-09-22
> **misterfixit said:**
> ...I want to build a sub net in the Shack using those three WiFi computers and have them fed by the WiFi adaptor which is plugged into the Wired Adaptor in the house.  At least I think this is how I should do it.

How about we look at it in a different manner?  I would make ALL of the PC's in the "shack" connect to the same subnet as what is in the house.  If you use a wireless AP (access point) you can have each PC in the "shack" connect via the AP.  Some wireless routers have a mode for running as an AP.

This is how my home network is set up.  All of my wired hosts connect to the DSL router via a switch.  The wireless AP also connects to the switch.  The wireless hosts connect to the network via the AP.  It sounds like that "adapters" are router/switch combination units.

In some instances the RF signal might not be strong enough for the distance.  In this case you will need to have an AP at either end with repeater capabilities. 

```
House:

Wired Router attached to Comcast Cable
PC #1 = 192.168.0.100
PC #2 = 192.168.0.111
PC #3 = 192.168.0.112
HP Laserjet 4000N = 192.168.0.113
HP Scanner/Printer/Fax = 192.168.0.114
Wireless Router = ???.???.?.??? **<--192.168.0.[COLOR="Red"]200**[/COLOR]

Shack:

PC #1 with WiFi card = **192.168.0.[COLOR="Red"]201[/COLOR]**

```

---

