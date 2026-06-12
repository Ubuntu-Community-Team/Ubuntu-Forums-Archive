---
title: "Dvb - atsc"
date: 2008-08-05
forum: Mythbuntu
---

### Post by Damanther on 2008-08-05
OK, I have a Mythbuntu 8.04 box with a Hauppage 150 installed and it has been working great for quite some time.

I was wanting to upgrade the tuner to something that would receive the digital broadcast here in the US.

I think I have confused myself reading all the wiki's though. If I am not mistaken the signal here in the us for over the air digital broadcasting is ATSC.

Lots of other places on this globe use DVB-T for over the air.

At this point I have become a little fuzzy.

OK, and we also have in the linux world a set of DVB drivers, which is not necessarily directly related to receiving DVB broadcasts. Some cards use the DVB driver, but can receive an ATSC broadcast.

What I can't tell from the linuxtv or mythbuntu wiki is which cards actually receive the ATSC signal even though they are using the DVB drivers.

For example, the DViCo FusionHDTV says the DVB drivers work out of the box for HDTV, but I can't find anything that verifies reception of the ATSC signal.

So the short question is which cards can receive the US ATSC digital signal? Preferrably one with a hardware encoder.

Damanther

---

### Post by newlinux on 2008-08-05
Sounds like you've got it right to me. DVB is a driver for digital tuner cards - not to be confused with non US (DVB-C, DVB-S, DVB-T) signals.

Digital (DVB) cards don't use hardware encoders because the stream is basically just captured digitally and doesn't need to be encoded. You only need (Well you don't really need, but use) hardware encoders with analog streams. That said, a good place to look for linux supported cards that can do ATSC OTA (8VSB):

[http://www.linuxtv.org/wiki/index.php/ATSC_Devices](http://www.linuxtv.org/wiki/index.php/ATSC_Devices)

this list is as comprehensive as I have seen.

I personally have used:

Kworld ATSC 110/115
pchdtv 5500
dvico fusion 5 lite

---

