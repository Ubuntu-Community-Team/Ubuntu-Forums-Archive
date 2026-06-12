---
title: "mythbuntu htpc configuration, help"
date: 2009-03-11
forum: Mythbuntu
---

### Post by vinalopo on 2009-03-11
Good evening, I am in process of assembling my new, first, htpc.

I want to be sure the hardware is fully compatible also because I am not experienced with mythbuntu and linux in general

my goal: audiophile audio, HD and use with dvb-s2 and dvb-t hd (I am living in Europe) tuner, low power consumption, almost no noise, reduced cost

My idea of configuration (please suggest a lot):

CASE + PSU	ANTEC	NSK2480
MOTHERBOARD	GIGABYTE	GA-MA78GM-S2H or GA-MA78GM-DS2H (please suggest)
CPU + FUN AMD 4850e + Scythe SCMNJ-1000P Ninja Mini	
SOUNDBOARD	ESI	JULI@
TUNER	Hauppauge	WinTV-HVR-4000
MEMORY		4GB
HD1	SEAGATE	BARRACUDA 250GB 
HD2	SAMSUNG	HD50 500GB
DVD-RW		ASUS DRW-2014S1 (SILVER): which to buy silent, cheap and easy to find?

please suggest your alternative proposals or give advice on this configuration

thank you very much

---

### Post by nickrout on 2009-03-11
DVB-S2 is not yet supported in mythtv, but may be in 0.22.

The hard drives sound big but if you have room for two why not max them out? Cost is naturally a factor, but I would be looking at putting in 2x750G or even 2x1TB if you can afford it.

Or if you can't put in one big HD and save your pennies until you can fill the other space with a big disk.

GIGABYTE GA-MA78GM-S2H and GA-MA78GM-DS2H both have an ATI video chipset, avoid this like the plague. Go for nVidia graphics chipset that can do VDPAU.

I cannot comment on the soundcard sorry.

---

### Post by Mikieboyblue on 2009-03-11
What is VDPAU? And should ATI gfx cards always be avoided? I personally do not feel nVidia cards perform all that well.

---

### Post by nickrout on 2009-03-11
> **Mikieboyblue said:**
> What is VDPAU? And should ATI gfx cards always be avoided? I personally do not feel nVidia cards perform all that well.

VDPAU gives linux access to the mpeg2 and h264 decoding and deinterlacing features on some nVidia graphics cards. This takes an enormous chunk of the load off the cpu. No similar technology is presently available on ATi or Intel graphics cards under linux.

nVidia cards have always worked better for mythtv, and VDPAU is the icing on the cake.

See the [wiki entry]("http://www.mythtv.org/wiki/Vdpau") for more info.

IMHO ATI cards should always be avoided for mythtv. They just don't have the drivers.

Don't forget that the video card in a HTPC has a different job and workload than in a gaming machine. Comparisons of video cards for gaming purposes are irrelevant. Comparisons under windows drivers are irrelevant.

Cheers.

---

### Post by vinalopo on 2009-03-12
thank you very much, great suggestion, really appreciated.

regarding hard drives, maybe I could put one 1TB, I would avoid heat and noise as much as possible, I can retrieve files from a separate NAS

can u suggest me a vdpau mobo? I haven't seen such specification in gigabyte, asus and asrock websites
I don't plan to add a separate video card so I would like having a good mobo, possibly with a similar price of the mobo I thought to put

---

### Post by manishmahabir on 2009-08-20
can someone suggest a good 5.1 or 7.1 soundcard supported in myth?

---

