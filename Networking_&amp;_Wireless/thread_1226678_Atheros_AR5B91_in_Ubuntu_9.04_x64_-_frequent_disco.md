---
title: "Atheros AR5B91 in Ubuntu 9.04 x64 - frequent disconnects"
date: 2009-07-29
forum: Networking &amp; Wireless
---

### Post by DarkED on 2009-07-29
Hi all, I need some help. I have a Gateway MD2614U laptop and it has an Atheros AR5B91 wifi chipset. This is a Draft-N chipset. I am using Ubuntu 9.04 x64. I am connecting to a Belkin F5D8236-4v1 wireless N router. I don't think this is a router issue because I don't have any problems in Windows.

The problem is, when I boot Ubuntu my wifi will connect and all will work fine... for about ten minutes. After that, it's frequent disconnects and I have to force it to reconnect each time. After doing this a few times it won't reconnect at all and I have to reboot to get it to connect again... and then I do the whole process over. For now I'm just booting into Vista since I can't figure this thing out.

Any ideas? Anyone know what driver this chipset uses by default, and if so, can I try another driver? Thanks for the help!

EDIT: The complete specs of the laptop in case you think it could be a hardware conflict:

AMD Turion x2 x64 @ 2.1ghz
3GB DDR2-667
250GB SATA3.0 5400RPM HDD
ATi Mobility Radeon HD3200
Conexant HD audio
Conexant modem
Marvell Yukon 88E8057 PCI-E Gigabit lan
Atheros AR5B91 b/g/Draft-n

---

### Post by lawhorne on 2009-10-31
I had this same problem and resolved it by installing:
linux-backports-modules-karmic

---

### Post by insanish1 on 2009-11-18
Thanks a tonne for this solution..was going mad with this problem! Have passed on this solution to one other friend of mine :) Thanks again!!

---

### Post by chambersc on 2009-12-18
> **lawhorne said:**
> I had this same problem and resolved it by installing:
linux-backports-modules-karmic

This worked for me! Thank you!

---

### Post by crazi2k on 2010-02-22
Were you able to get the N-channel router running @ 40 Mhz wide band to work with the ARB591 client/laptop?

For some reason it won't connect to N-channel (works on wireless G) & i'm not sure how to move forward to a resolution. My N-network (LinkSys 600N Router) does not have any security & it controlled by MAC access list. Tried the linux-backports-modules & the mad-wifi driver Ath5k

I would highly appreciate if someone could send me specific instruction to have it work. I'm running Karmic Koala on 2.6.31-16 kernel

---

