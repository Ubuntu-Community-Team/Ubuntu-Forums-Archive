---
title: "Mythbuntu on Pentium4 Dell budget box?"
date: 2011-08-20
forum: Mythbuntu
---

### Post by natgab on 2011-08-20
I have been wanting to make a HTPC on a very cheap budget. I currently use my main computer (in signature) to watch streaming movies, DivX videos, etc but only on my 19" 720p monitor.  I don't want to move my main computer to the living room with my 37" 1080i HDTV, so I wanted to know if using a cheap Dell business PC would work OK. *Any tips or caveats?*

I would like to use Mythbuntu to manage my media, though not really use it as a DVR.  I mostly want to be able to see streaming TV shows / movies or play ripped movies in some Divx/AVI/H.264 codec.  I found the PC below incl s/h, for around $60.00 USD on eBay.  I doubt the stock video would work, but having a PCIe should make it easier to find a cheap ($30.00 USD) HDMI video card.  It also has SATA, so I could add a bigger HD, though I have a spare external HD to connect to it.


Example: Dell Optiplex GX280 P4 3.0ghz 1GB RAM / 40GB HD SATA / PCIe slot. Slim, small desktop and med desktop same price.
Note: **I am not set on a Dell, there seem to be many HP and IBMs too at this spec/price point.** 

thanks

---

### Post by bance on 2011-08-20
Should be ok, I use a celeron D 2.8ghz as a backend serving 4 frontends...

If you get an Nvidia VDPAU capable video card you should be able to watch most content easily, it is better to have a beefy CPU for a frontend so that there is enough grunt to watch anything using software though!

---

### Post by David Grigor on 2011-08-23
Having a PCI express slot is key. You will need to add a nvidia card if your going to use as a front end with hdmi connectivity for TV. Nvidia GT 220 or 520 ( more current model ) is sufficient and run about $50.

I have a 2008 vintage Dell w 1.8 celeron and as long as you have a decent video card it runs fine for frontend.  I don't use it for backend but as long as all digital and not planning to do any transcoding then should be okay.

---

### Post by natgab on 2011-08-24
I will check the Dell site more to compare models.

I wanted to know if they were good enough since my brother actually has a Dell GX 260 with a 2GHz chip? but an older add-on video card and I think a smallish 60GB HD.  He doesn't use it for HTPC tough, it is the kids PC.

I think his has an IDE HD and only an AGP slot for video card, so that is probably why his is a bit sluggish. I will pass by his house and read the specs to compare how his PC works playing some Divx to see the performance.

Thanks for the information, I will update on how it goes.

---

### Post by LowSky on 2011-08-24
If you buy used, don't buy anything older than 3-4 years old.

---

### Post by natgab on 2011-08-25
> **LowSky said:**
> If you buy used, don't buy anything older than 3-4 years old.

---Is it because of compatability or reliability?  I think the times I have bought used they have been about 5 years old or less.

I actually just got an old Power Mac G4 533MHz Digital Audio, leftover from work.  I might try to use it.  But will have to review the specs to see if I can use it.  I could watch some videos on it using VLC, but I don't know if it will work for streaming.

And since it's a PPC Mac, I will probably have to move over to regular Debian or Debian MintPPC.

EDIT: Tested the Mac, I guess a 10 year old Mac isn't going to cut it. I will have to stay with plan A and get me one of those cheap Dells from eBay.

---

### Post by newlinux on 2011-08-28
It could work, but you also might want to check into how quiet it is... I've used a couple of Pentium 4s for front and backends (have on in the garage now). But it's not the quietest thing and would never be used as a frontend inside the house. I use it in the garage with headphones on when I'm working out...

---

### Post by LowSky on 2011-08-28
For me buying used is a waste as even today's budget boxes could destroy a old PC in terms of speed. Why pay $200 for an old PC when you can build a new one for just as much using low spec parts.

---

### Post by newlinux on 2011-08-29
> **LowSky said:**
> For me buying used is a waste as even today's budget boxes could destroy a old PC in terms of speed. Why pay $200 for an old PC when you can build a new one for just as much using low spec parts.

I'd agree, but natgab said he could get it for $60.

---

### Post by nickrout on 2011-08-29
Anything that has a pcie x16 slot will work with an nvidia card to give very good quality video. Just make sure there is room for the chosen card.

I use a HP Compaq dc7100 SFF in this manner, works well and has both pcie x16 and sata.

However if you don't want to record TV mythtv is not what you want. Use xbmc, which will also give you nvidia acceleration.

---

### Post by mr_luksom on 2011-08-31
+1 on the GX280 - I use it as a FE. No issues whatsoever for 720p/1080i. I paid $60 for mine, and it is perfect.

---

### Post by PatrickD-52761 on 2011-09-03
I'd like to toss my two-cents in here also.  My backend/frontend is a homebuild that I did in 2003. It has 2GB of RAM (PC2100) and an AMD Athalon XP 1800+ with an ATI Radeon 9550 card in it. The tuners on the cards (Hauppage HVR-1600) handle the processing for the videos, so that's more than enough for recording (although I haven't tried watching live TV while recording another show yet).  It has, however, been recording two shows at one time on a regular schedule (typically Tuesday nights in the past viewing season). I also haven't tried hooking it up to an actual television yet, so your mileage may vary.

I put a new power supply in, so it's quieter than you'd think (although it's not silent by any means). And it has regular PCI slots+ and AGP 2/4 slot for the video card.

Anyhow, my point is that while newest is better, you CAN make an older computer work (if nothing else, until you can afford something newer). It may not be awesome, but it is doable. 

Have a great weekend, and best of luck with your setup :)
Patrick.

---

### Post by natgab on 2011-09-05
> **LowSky said:**
> For me buying used is a waste as even today's budget boxes could destroy a old PC in terms of speed. Why pay $200 for an old PC when you can build a new one for just as much using low spec parts.

---The thing is that those small form factor boxes fit really nice and out of the way for the price.  If I try using those small cube boxes (Apevia type) they cost more and using one of those netbook desktops isn't worth the hassle.  I wouldn't use an Atom based if I use something new.

I currently got my old Thinkpad X40 to play videos, but I need speakers since it only a a tiny 1" speaker :P

---

