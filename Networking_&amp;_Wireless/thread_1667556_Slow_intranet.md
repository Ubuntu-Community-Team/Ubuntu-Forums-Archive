---
title: "Slow intranet"
date: 2011-01-15
forum: Networking &amp; Wireless
---

### Post by John Long on 2011-01-15
Just out of curiosity: I have a new Qwest DSL router plugged up to three computers all connected with cat6. Why do my intranet transfers always top out at around 7.2-7.9 MB/sec. Shouldn't it be somewhat faster? All computers are running 10.4 or 10.10. All pretty new and speedy.

---

### Post by John Long on 2011-01-19
Is this normal? Is there anything I can do to speed it up a bit?

---

### Post by mips on 2011-01-19
Fastest max througput on 100Mb/s ethernet is about 11.5MB/s but this could easily be less.

Things that might influence the speed are the chipset used by your qwest router.

Do a little test and directly connect two of your computers and set the speed to 100Mb/s & the duplex to FULL to see what speeds you can get without the router. If you get higher speeds you know the router is the bottleneck.

Manually set the speed & duplex on all your pcs to 100Mb/s FULL Duplex when testing with the router.

If your pcs support gigabit ethernet buy a gigabit switch and connect your pcs to the switch and the switch to the router as interlan communications rely on layer 2 of the osi model thus mostly bypassing the router except for traffic destined to the internet.

---

