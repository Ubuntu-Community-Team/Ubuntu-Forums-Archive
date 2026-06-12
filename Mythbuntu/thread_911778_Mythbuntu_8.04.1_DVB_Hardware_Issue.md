---
title: "Mythbuntu 8.04.1 DVB Hardware Issue"
date: 2008-09-06
forum: Mythbuntu
---

### Post by simon_ives on 2008-09-06
Hi All, I'm having a minor hardware issue that I hope someone can help me with.

Yesterday I decided to make my wife's Windows XP based desktop dual boot Mythbuntu 8.04.1 so that I'd have access to the media on my file server via a media centre interface in the bedroom.  I've got Mythbuntu 8.04.1 running fine in the living room, but with a different dvb card. Mythbuntu installed fine except two things.  The first is that I'm as yet unable to configure widescreen support for the ATI card, but I can get this fixed on my own.  What's got me stumped is the DVB card.

The card is a DViCO FusionHDTV DVB-T Lite, a bit old but is supposed to work 'out of the box' with stock kernels since 2.6.9.  Mythbuntu, however, doesn't seem able to see the card.

The relevant section of lsmod reads:

Module | Size | Used by

dvb_bt8xx | 17796 | 1
dvb_core | 81404 | 1 dvb_bt8xx
and
bttv | 175860 | dvb_bt8xx bt878

So the modules seem to be there.

If I cd into /dev/dvb/ a single adapter is listed as adapter0

However, upon dmesg | grep dvb I get:

[   41.072890] bttv0: add subdevice "dvb0"

Any suggestions and/or help would be much appreciated.

---

