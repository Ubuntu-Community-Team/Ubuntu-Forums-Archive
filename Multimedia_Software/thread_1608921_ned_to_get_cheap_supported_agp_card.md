---
title: "ned to get cheap supported agp card"
date: 2010-10-29
forum: Multimedia Software
---

### Post by jturner49 on 2010-10-29
I have about 60 old PC's that have an 8X AGP slot. What used/old AGP video cards are there that are supported, that are cheap and will provide a 1280x768 (or there abouts) for a generic lcd wide screen display?

I've seen several Dell nVidea 5200 w/64mb AGP cards for under $10... Will that work? What does?

Thanks!

Joe

---

### Post by MartyBuntu on 2010-10-29
The NVIDIA 5200 series cards can support widescreen resolutions, I'm pretty sure. I have a few on the shelf (FX5200) but none installed in any machines since 7.04, so I can't be %100 positive.
Hopefully someone else can chime in.

---

### Post by james_xxx on 2010-10-29
One AGP card that would be hard to beat, in my opinion, would be any **ATI Radeon 9600**-based adapter.

These cards work great using FOSS drivers, right out of the box, providing compiz/Kwin compositing and the works, at least as long as the resolution does not get extremely high. I can attest that at 1280x1024 on down, things are fine. 

I have several machines using this card, and have been really impressed.

---

### Post by sleepingdragon on 2010-10-30
I was using a FX5200 up until last week with a resolution of 1440x900, all on an AGP x8.

Absolutely no problems at all, the repo drivers worked a charm.

---

### Post by P4man on 2010-10-30
FX5200 (and all 5 series) only work with the legacy 173 series of binary nvidia drivers (and probably nouveau driver, but those arent too great yet). Legacy drivers probably will work fine, but its not exactly impossible in the near future nvidia will drop support for those cards. Perhaps a geforce 6 series like a 6200 is a safer bet, they are still supported by the latest drivers and I cant imagine them costing a lot more.

As for the ATI alternative.. once bitten, twice shy. Ive encountered far too many headaches with older IGPs and newer discrete cards from ATI, both with oss drivers and catalyst drivers to be able to recommend them in good conscience.

---

### Post by cascade9 on 2010-10-30
+1 to P4mans idea of a 6200 (or a 6600/7300/7600) but if your after 60 of them, even a small increase in cost could really add up. 

FX-5XXX cards should work just fine, and even older GF 4 Ti, GF4 MX GF3 and GF2 cards should work. I dont know if earlier cards will do widescreen, never tested them. 

The only issue with older cards is possible loss of support. Already, with newer version of ubuntu the 96.xx drivers are 'waiting' for nvidia to make the drivers work with oxrg 1.9. The 71.xx drivers will never get a version that works with xorg 1.9. Something to keep in mind. BTW, here is what drivers support- 

71.xx- Vanta-> Geforce 256. 
96.xx- Geforce2 -> Geforce4
173.xx- FX. 
195.xx (and higher)- Geforce 6 to current GTX4XX.

---

### Post by jturner49 on 2010-10-31
[SIZE=1]**[COLOR=black]Well I ordered a used [/COLOR]**[/SIZE][COLOR=#000000][FONT=arial][B][SIZE=1][B][COLOR=black]Dell nVidia GeForce4 MX440 64MB AGP 8X DVI for around $10 to evaluate. There seem to be plenty more at that price. 
I want to use Ubuntu 10.10 32b and understand there is a Xorg 1.9 "bug".
Sigh..... 1366x768 (16:9) seems like a reasonable[/COLOR] goal for a "cheap" card....
Does anyone have any other suggested cards?
Thanks!!
Joe

[/B][/SIZE]
[/B][/FONT][/COLOR]

---

### Post by cascade9 on 2010-10-31
You'd be better of with a FX5200 over a GF4MX440.

---

