---
title: "Newbie with DVB-S scan problems."
date: 2008-11-09
forum: Mythbuntu
---

### Post by sam667 on 2008-11-09
Hi,

I've just set up my first MythTV server/front with a Hauppage DVB-S (budget) in it.
Getting the server to find the card was a right nightmare but I got there in the end... so now when I run dmesg I get:

[   11.138584] saa7146: register extension 'budget_ci dvb'.
[   11.139552] budget_ci dvb 0000:02:06.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   11.139593] saa7146: found saa7146 @ mem f89bc000 (revision 1, irq 22) (0x13c2,0x100f).
[   11.139605] saa7146 (0): dma buffer size 192512
[   11.139610] DVB: registering new adapter (TT-Budget/WinTV-NOVA-CI PCI)
[   11.185039] adapter has MAC addr = 00:d0:5c:22:29:5e
[   11.185742] input: Budget-CI dvb ir receiver saa7146 (0) as /devices/pci0000:00/0000:00:1e.0/0000:02:06.0/input/input6
[   11.656260] DVB: registering adapter 0 frontend 0 (ST STV0299 DVB-S)...

I've also managed to scan for transponders and have a ~/.szap/channels.conf file.

However I cant get MythTV to scan the channels... I've googled the problem all day but cant get anywhere with it... 
Could anyone help?

Cheers
Sam.

---

