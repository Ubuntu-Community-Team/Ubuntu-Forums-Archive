---
title: "no signal on mythbuntu 9.10"
date: 2009-12-05
forum: Mythbuntu
---

### Post by sourcefinder on 2009-12-05
I installed mythbuntu 9.10 on a E5200, 1 Gb RAM, 160 Gb harddisk. I use a Pinnacle PCTV SAT CI (version 1.1) to use the mythtv function. This card is directly connected to my LNB (location: Netherlands). n capture card setup i've installed it as a DVB DTV capture card (v3.x)/ The DVB device number is /dev/dvb/dapater0/frontend0. Frontent ID: DST DVB-S, subtype: DVB-S. The DiSEqC is configured as LNB, Universal Europe. I use no grabber; the channel frequency table is europe-west. When I scan for channels on frequency 12575 (BVN) or 11053 (couple of german programs), I get a 'no channels found - no signal' message. The polarity is horizontal, symbol rate 27500000 (default), FEC: auto, Inversion: Auto. 
 
Of course I experimented with other settings, but the result stays the same. Can anyone help me out? Thanks in advance!
 
SOLVED: setting the symbol rate to 22000000 solved the problem!

---

