---
title: "Recommendations for New Video Card please."
date: 2011-05-03
forum: Multimedia Software
---

### Post by Robbyx on 2011-05-03
I have 2 monitors running off a GeForce 7600cs 256mb DDR2 card. I wouldn't mind a third monitor.

I do not play games or stream to my TV, but I do look at videos on the monitors, and have video internet meetings using skype and am considering yahoo messenger for the same purpose.

I am thinking it is time I upgraded my video card. The GeForce can run SLI. I assume SLI means that I can use 2 cards in the computer and have them linked so that they run much faster. Also each would have 2 digital connections so  could I go up to 4 monitors?

I hoping I can get some advice as to What cards should I go shopping for? I assume they have to be Nvidia. As for budget I can see the expensive cards have gaming and connection features that I do not need. So I propose about $60 unless there is something more expensive that is really worth the money for my situation.

Please comment,

Robin

---

### Post by Robbyx on 2011-05-04
Any chance of a reply? I don't mind a second hand card.

---

### Post by BicyclerBoy on 2011-05-04
For best video decode/playback & HDMI audio
(all PCI-e)

GT430  (3d BR decode ready AFAIK, HD audio over HDMI works)
GT240 
GT220 (excellent video/price/size but 430 is better choice)

IMHO You are better to spend the money on the GT430..

---

### Post by Robbyx on 2011-05-05
> **BicyclerBoy said:**
> For best video decode/playback & HDMI audio
(all PCI-e)

GT430  (3d BR decode ready AFAIK, HD audio over HDMI works)
GT240 
GT220 (excellent video/price/size but 430 is better choice)

IMHO You are better to spend the money on the GT430..

Thank you for taking the time to advise me.

I looked on ebay and there are 1, 2, and 3 gb memories on these cards. Will it be worth me going for the 2 or 3 gb? it is about another £40.

On the CLI point. How do I link cards together to take advantage of the CLI? I am assuming it will be sensible to keep my old card for the cli benefit?

---

### Post by BicyclerBoy on 2011-05-06
For video decode VDPAU 512MB is okay.
The video cards I listed are HTPC video decode recommendations.

The memory speed prob only matters for openGL performance not VDPAU.

SLI (Linux) only works on matching h/w or very similar/specific pairs. 
Check the nvidia linux driver readme...

The latest gen video cards have full VDPAU capability but the old GTX200s do not.

If you also want game openGL performance get a GTX 400 or 500.
These will burn a lot of power/noise/air/dust/cost/PSU.

The GT240 is not a slug but it is not a super gaming card.
The GT430 is the best HTPC card.

---

### Post by Robbyx on 2011-05-06
Do I understand you correctly that you are advising that for my non gaming but video applications there is no need for the memory in the 430 to go above 512mb?

It also seems that there is no point in keeping the old card.

I looked at a picture of the video out on the card and it seems that there is only one digital and the other analogue. I am using two digital screens. It occurs to me this may be a manufacturer feature. Do you know any which have 2 or even 3 digital connections?

Thank you again for your help.

---

### Post by BicyclerBoy on 2011-05-06
512MB was the minimum recommend for VDPAU HD video decode/presentation.
It may not have been a hard limit, may have been driver related..More RAM does not hurt just costs. Different RAM types DDR2 & 3 influence clock speed & power.

From my looking..
most new video cards seem to have 1xHDMI, 1x DVI-I & 1x VGA (Dsub).

DVI-I is dual link DVI-D & VGA (DVI-A) in the same conn
So you get 2 digital connections & 2 analogue connections but not at the same time.

The HDMI is electrically equivalent  to single link DVI (fine except for really big screens).
A $5 adapter is avail HDMI-to-DVI-D (single link), may come with card..

I think that some video cards support a splitter on the DVI-I to have 2 screens (1 VGA + 1 DVI-D); try getting that working with linux driver/Xorg..


A GTS 450 good be a good buy if you want a better gaming...
A pair of GTS 450 can run in SLI mode..

All of the 7000 series were HTPC video dogs expect for one model 7900.

---

