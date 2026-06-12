---
title: "Jensen Fast Ethernet pcmcia FastEthernet Card not working at 100 mbit"
date: 2009-06-23
forum: Networking &amp; Wireless
---

### Post by Neonlajt on 2009-06-23
Hi,

I`m having a major problem with one of my network adapters.
Its the Jensen Fast Ethernet pcmcia card.
It says both in mii-tool and on the other computer connected to it that it negotiates on 100 mbit, though I am maximum getting 1.3 mb/s = 10 mbit when transferring.

I`ve tried several things though.
As of now, the card is a NE2000 compatible card and uses the axis_cs module (and I have blacklisted pcnet_cs and 8930). 

I`ve tried to blacklist that module and only use the pcnet_cs with the 8390 module (which is the instructions from the vendor). Though then mii-tool does not work at all. And the worse part is that  I get even shittier transfer speeds (6-800 kb`s). Its apparent that it autonegotiates with both modules on 100 mbit, even though the actual output is far 10 mbit. 

I`ve also tried to manipulate it with ethtool, but it is not supporting my card (getting no info available on card). This I have tried with both modules.

I`ve also tried to set the speed in the modprobe.conf with the options command in a text file, not giving any results.
Tried different cables, different computers and still nothing... It is extremly annoying.

Also there is another built-in network card on the laptop which is able to send files at full 100 mbit speed.

Can it be the physical "speed" of the pcmcia port that is not high enough to support the rate of 100mbit?

Cheers

---

