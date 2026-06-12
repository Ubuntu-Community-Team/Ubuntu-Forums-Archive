---
title: "[SOLVED] NVidia 8600 graphics card:Will it play on a 350W power supply unit?"
date: 2007-12-26
forum: Multimedia &amp; Video
---

### Post by sdim on 2007-12-26
Dear colleagues,Merry Christmas to everyone.

I'm interested in buying A 8600GT graphics card but some friends suggested that it will have a problem working properly on a 350W power supply unit.

Please,any opinions are valuable.Thank you.

---

### Post by tgalati4 on 2007-12-26
The 8600GT (pci-e version) does not require extra power connectors as it draws power directly from the motherboard.  I know it works well with a 500 watt Antec powersupply and this particular computer (C2D E6750, 2x500 GB Hitachi DeathStar drives, 1 nVidia 8600GT card) draws about 120 watts during normal operation and perhaps 150 watts peak.  

I would guess that 350 watts is marginal depending on what else is in the machine.  If it is a good quality power supply then it shouldn't be a problem.  If it's a consumer-grade Dell or eMachines, then I would expect problems.

Frequent lockups during gameplay would be a clue, but in Linux you can install lm-sensors and monitor the voltage levels of the 5V and 12V lines and see if they dip during heavy use.  There are several temperature/voltage viewers in Windows as well, but I don't use Windows anymore so I can't help you there.

---

### Post by sdim on 2007-12-26
You've been most enlightening.Thank you.

---

