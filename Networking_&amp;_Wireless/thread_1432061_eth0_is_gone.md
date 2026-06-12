---
title: "eth0 is gone"
date: 2010-03-17
forum: Networking &amp; Wireless
---

### Post by Mucus on 2010-03-17
Ok, so i have Ubuntu studio 9.10 installed as on OS and thus I hope I posted it to the right place.


My eth0 has dissappeared overnight. Iwconfig lists it not, and neither does ifconfig.
Sudo lshw -C network shows the following

network UNCLAIMED
description : ethernet controller
Product: BCM4401 100Base-T
Vendor : Broadcom Corporation
Physical id: 2
bla
bla
bla
bla
...

(had to write some snippets here as I cannot connect to internet)

lspci also detects the hardware.
Graphical interfaces (the network tools) do not identify eth0, and it is also not present in the /dev directory.

From this I deduct that the driver is an issue. I have tried the module E100, but it does not work. It's definately a 100mbs card, so ok, E1000 also works not, and thus it as a surprise... comes NOT.

I could not find any drivers relating to 100base-T.

Perhaps the problem is that I removed the ndiswrapper module yesterday? Although the eth0 connection has been running smoothly since installing Ubuntu Studio. I don't think it uses ndiswrapper by default after install. Am I wrong here? Did I just remove some fancy setup by purging ndiswrapper?

I have not purged any other modules, so the driver should still be here somewhere.. unless of course it was the ndiswrapper.

Clues anyone? I read several articles on this issue under Ubuntuforums but they did not, unfortunately, work for me

---

### Post by Mucus on 2010-03-17
Problem is solved. I was using the wrong drivers and in addition did not realize to add the module to the list of modules to be loaded on boot.

---

