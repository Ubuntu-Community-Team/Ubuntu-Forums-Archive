---
title: "Gigabit ethernet, one missing pin"
date: 2013-01-29
forum: Networking &amp; Wireless
---

### Post by Diderik From on 2013-01-29
Hi!

I have tried several times to crimp/terminate a Gigabit ethernet CAT6 cable. Each time the network checker cannot find a signal on pin 7. However, when connecting the cable directly between two Gigabit laptops, iperf gets 900+ Mbps. Which is rather good, right? (When the connection goes through my supposedly gigabit router to my supposedly gigabit NAS, I get far less, but I suppose this is hardware, not cable, related?)

Is it all possible to get 900+ with one missing pin? (The same as when I connect a store bought, pre terminated CAT6 between the two. The network checker reports all 8 pins on this one). And, I was planning to use PoE on this cable. Let's say pint 7 is out of order, will PoE be possible?

(The cable goes behind some newly installed stucco, inside newly wallpapered walls and cannot be exchanged. This is what I have got to work with...)

Any thoughts?

Thank you,
Diderik

---

### Post by craigcrawford114 on 2013-01-29
According to: [http://en.wikipedia.org/wiki/Power_over_Ethernet#Powering_devices](http://en.wikipedia.org/wiki/Power_over_Ethernet#Powering_devices)

In mode **A**, pins **1 and 2** form the positive charge, while pins **3 and 6** form the negative.
In mode **B**, pins **4 and 5** form the positive charge, while pins **7 and 8** form the negative.

As long as you operated in mode A there would be no problem with PoE, but mode B would likely operate at half the voltage/current.

Without pin 7, you'll not have a 4th pair. I've never had to deal with such a situation and personally, I'd just remake the cable until I got it right or replace the cable (**There could be a fault with the cable itself, not the connector**).

Just make sure you are pushing the wires in securely and have gave the crimper a good solid squeeze.

---

### Post by Diderik From on 2013-01-29
Thanks for your answer! Yes, I suppose it's the cable and not the connector, after that many crimp attempts, I should have gotten one right. I'll have to check the specs on the PoE wireless gateway I'm considering: [http://www.ubnt.com/unifi](http://www.ubnt.com/unifi)

Thanks!

---

### Post by tgalati4 on 2013-01-29
Most Cat5/6 cable has a pull rating of 35 lbs.  If you exceed that you can stretch the copper and possibly break one of the lines.  Is this USA-made cable or catfood?

Most routers will try to maximize signal through whatever signal pairs are working.  Too many bit errors will result in dropping to 100 MBit/sec speeds.

---

### Post by craigcrawford114 on 2013-02-01
I never buy stranded cable ever. Solid core is more expensive but it's more robust and probably carries the signal better. One solid core and less air, most of stranded cable has a lot of air in it.

---

