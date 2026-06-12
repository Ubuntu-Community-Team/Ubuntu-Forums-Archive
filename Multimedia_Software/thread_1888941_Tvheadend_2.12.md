---
title: "Tvheadend 2.12"
date: 2011-11-30
forum: Multimedia Software
---

### Post by aasgaa on 2011-11-30
I have the following running Tvheadend installation:
•    Ubuntu server 10.04 (Lucid Lynx)
•    Kernel version 2.6.32-33-generic-pae
•    KNC1 TV-Station DVB-C Plus card

I have finally managed to add a ”TechniSat SkyStar HD2” card  (DVB-S/S2) and make it work under  Ubuntu (with scan and w_scan)

Next challenge: How to make it scan for muxes/channels under Tvheadend?

Info from the web-interface of Tvheadend:

[SIZE=3]**Hardware**[/SIZE]
**Device path:**
/dev/dvb/adapter0
**Device name:**
STB0899 Multistandard
**Host connection:**
PCI
**Intermediate Frequency range:**
950000 kHz - 2150000 kHz, in steps of 0 kHz
**Symbolrate range**:
5000000 Baud - 45000000 Baud
**[SIZE=3]Status[/SIZE]**
**Currently tuned to:**
12,551,500 kHz Vertical (No satconf)
**Services:**
0
**Muxes:**
1
**Muxes awaiting initial scan:**
1

Any suggestions how to proceed?

---

### Post by aasgaa on 2011-11-30
This was an easy one. 
I changed from "Astra-19.2E" to "Astra-23.5E" - and it works :-)

---

### Post by borsdel on 2012-01-07
Thanks for the hint. Had the same problem with my STB0899 tuner.

---

