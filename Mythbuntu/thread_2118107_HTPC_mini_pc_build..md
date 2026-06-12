---
title: "HTPC mini pc build."
date: 2013-02-20
forum: Mythbuntu
---

### Post by Cryxo on 2013-02-20
HI guys I need an advice about my upcomming setup :

Getting and Nvidia gt210 [http://www.alza.sk/graficke-karty/podla-cipu/nvidia/18849879.htm#f&pg=1&pn=1&po=1](http://www.alza.sk/graficke-karty/podla-cipu/nvidia/18849879.htm#f&pg=1&pn=1&po=1) 

Low budget Ivy Bridge 2,6 dual core [http://www.alza.sk/intel-celeron-g1610-d380184.htm](http://www.alza.sk/intel-celeron-g1610-d380184.htm)

SSD disk, 4 gigs of ram, 

23-24 inch screen for example : [http://datacomp.sk/led-philips-239c4qhsb-23-_d131973.html#.USWDJjcipyF](http://datacomp.sk/led-philips-239c4qhsb-23-_d131973.html#.USWDJjcipyF) scroll down for specs.


Browsing, watching youtube and mostly internet videos on this screen will it be good enough ? Also I need a MOBO and Wireless keyboard advice that will work with linux, thx for all responses !

---

### Post by BicyclerBoy on 2013-02-20
Avoid GT210..it is inadequate for any video post processing/openGL like de-interlace/scaling/denoise/sharpen etc.

The GT210 is okay if you have low expectations & will never watch interlaced video (broadcast).
But a GT610 or GT520 are a much better cheap option.

The integrated ivybridge HD graphics (& VAAPI) are probably better. Just use the later kernel & intel driver/VAAPI before buying any graphics card..

Better nVidia choices are: (worst to best)
GT520
GT610  (could be = to 520)
GT220
GT430/GT620
GT240  (full height, over-powered for HTPC)
GT630

---

### Post by gordintoronto on 2013-02-21
That would probably make an adequate HTPC. An SSD speeds up booting and program loading, and an HTPC doesn't do a lot of either, so it's somewhat wasted. A big, 7200 RPM hard drive is more appropriate, maybe 2 TB.

If you decide to try using the CPU-based video, make sure the motherboard has HDMI.

I would be tempted to try an ITX form factor case and motherboard. If you intend to install a blu-ray drive, make sure the case has room for it.

I highly recommend the PCMech web site once you have a full list of components, but before you buy anything. They will probably tell you, "get a better power supply."

That monitor doesn't have the greatest reviews. You could even consider a small 1080P LED TV if you can get signals over-the-air where you live. Eg:
[http://www.samsung.com/us/video/tvs/UN22D5003BDXZA-specs](http://www.samsung.com/us/video/tvs/UN22D5003BDXZA-specs)

---

### Post by Cryxo on 2013-02-21
Thx for advice I was looking at those GT610 before so I look more. This card look great [http://www.alza.cz/EN/evga-geforce-gt520-s-integrovanym-dvb-t-tunerem-d330799.htm](http://www.alza.cz/EN/evga-geforce-gt520-s-integrovanym-dvb-t-tunerem-d330799.htm). Btw what about AMD ? How is it with drivers nowadays on them ? Stil the same ?

---

### Post by Cryxo on 2013-02-21
> **gordintoronto said:**
> 

I highly recommend the PCMech web site once you have a full list of components, but before you buy anything. They will probably tell you, "get a better power supply."

That monitor doesn't have the greatest reviews. You could even consider a small 1080P LED TV if you can get signals over-the-air where you live. Eg:
[http://www.samsung.com/us/video/tvs/UN22D5003BDXZA-specs](http://www.samsung.com/us/video/tvs/UN22D5003BDXZA-specs)

I check the site thank you :) Yea that was just an example I will digg for it too.

---

### Post by Cryxo on 2013-02-21
Anyway anyone have experience with this ?
[http://www.hardkernel.com/renewal_2011/products/prdt_info.php?g_code=G135341370451](http://www.hardkernel.com/renewal_2011/products/prdt_info.php?g_code=G135341370451)

---

### Post by jksj on 2013-02-21
It looks like an ARM processor. Although UBUNTU runs on it, Mythbuntu is not yet available for this platform.

---

### Post by PhilWig on 2013-02-22
> This card look great [http://www.alza.cz/EN/evga-geforce-g...em-d330799.htm](http://www.alza.cz/EN/evga-geforce-g...em-d330799.htm)
I could find no information about the tuner on that card.  It is very important that it has stable drivers in Linux.
You might prefer a dual DVB-T card?

Phil

---

### Post by Cryxo on 2013-02-22
Nah I ll just go with one of these [http://www.alza.cz/EN/graficke-karty-s-cipem-nvidia-geforce-gt610/18854068.htm](http://www.alza.cz/EN/graficke-karty-s-cipem-nvidia-geforce-gt610/18854068.htm) which one should I buy ? With passive cooling.

---

### Post by topcat5 on 2013-02-23
> **Cryxo said:**
> Nah I ll just go with one of these [http://www.alza.cz/EN/graficke-karty-s-cipem-nvidia-geforce-gt610/18854068.htm](http://www.alza.cz/EN/graficke-karty-s-cipem-nvidia-geforce-gt610/18854068.htm) which one should I buy ? With passive cooling.

I'm not sure what case you are getting, but with ITX form factor keep in mind those passive cooled cards take up a lot of room.  It's why I didn't go with one when I built an ITX system. I couldn't find one that fit.  At the time I went with a PNY 1/2 height GT430.

---

