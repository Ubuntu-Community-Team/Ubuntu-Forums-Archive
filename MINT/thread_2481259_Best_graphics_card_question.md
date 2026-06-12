---
title: "Best graphics card question"
date: 2022-11-23
forum: MINT
---

### Post by f23948 on 2022-11-23
I am using my Dell Optiplex 9020 mini tower, I am using Linux Mint Cinnamon non-Debian edition, please I would like to know where I can find and buy my best graphics card?

---

### Post by QIII on 2022-11-23
Moved to MINT.

Your "best graphics card" may be influenced by driver modules available.  The "MINT non-debian" distribution is not Ubuntu, so we can't speak to driver module availability.

---

### Post by exploder on 2022-11-23
I have a 2 GB NVIDIA GT 1030 running under Linux Mint Cinnamon Edition. AMD makes some decent low end cards too and usually work out of the box as long as it's not something just released. You need a card that doesn't use much power because you are limited somewhat by the power supply and available connectors. Something that just needs the PCI slot on the board is ideal. AMD has better Linux support in my opinion. NVIDIA cards are a real pain in the ### sometimes under Linux. I mentioned the GT 1030 because you can find a new one dirt cheap, does work in Mint with the latest proprietary drivers, runs cool, and it's the only card I could think of at the moment that would work with your other hardware.

I should mention, I do not screw with kernel or graphics card drivers on that system. Not an ideal situation but kernel updates tend to break NVIDIA drivers constantly... Something like maybe an AMD RX 550 might be the safest choice.

---

### Post by f23948 on 2022-11-23
can i game in [s]Ubuntu[/s] with amd graphics card?

---

### Post by f23948 on 2022-11-24
I mean Linux Mint not Ubuntu

---

### Post by exploder on 2022-11-24
You should be able to on Steam.

---

### Post by f23948 on 2022-11-24
> **exploder said:**
> You should be able to on Steam.

Oh ok thank you for reply. Can I able to on steam without driver with kernel?

---

### Post by f23948 on 2022-11-24
> **exploder said:**
> You should be able to on Steam.

Can i light gaming such as mupen64plus, etc. without driver witth kernel?

---

### Post by exploder on 2022-11-24
AMD graphics use the open source driver, no need to install or change anything. It would be light gaming because of your system specs. I can not recall having issues with AMD or Intel graphics with Mint or it's parent, Ubuntu. I have an AMD RX 570 in my Ubuntu 22.04 system and it worked fine out of the box. At any rate, an AMD graphics card would make light gaming possible and you don't have to worry about breaking the driver from an update gone wrong.

---

### Post by f23948 on 2022-11-24
> **exploder said:**
> AMD graphics use the open source driver, no need to install or change anything. It would be light gaming because of your system specs. I can not recall having issues with AMD or Intel graphics with Mint or it's parent, Ubuntu. I have an AMD RX 570 in my Ubuntu 22.04 system and it worked fine out of the box. At any rate, an AMD graphics card would make light gaming possible and you don't have to worry about breaking the driver from an update gone wrong.

Thank you for reply. Please i would like to know where i can find and buy amd graphics card? i have $60 budget

---

### Post by oldfred on 2022-11-24
I had a $60 video card about 8 years ago. Put it into new build in 2014.
Later checked specs and found the CPU's video was twice the video card. 
[https://www.videocardbenchmark.net/](https://www.videocardbenchmark.net/)

So review the specs of your CPU's video and any card you are considering.
May be better to save up for much better card if really into gaming.
[https://www.tomshardware.com/reviews/best-gpus,4380.html](https://www.tomshardware.com/reviews/best-gpus,4380.html)

---

### Post by TheFu on 2022-11-24
I fear the case is the real limiting factor ... and the extremely low budget.  

Pre-COVID, my nvidia 1030GT was $70.  That's a 4 yr old GPU now and 2 months ago, they were running $120!
People have been getting burned by fake GPUs at low prices for a few years.  There are methods to flash the GPU firmware so it lies about the model, RAM, etc.  

+1 for using AMD, but I wouldn't know where to find one for $60.  Just searched a local computer store.  They are selling 
"Visiontek AMD Radeon HD 5450 Passive Cooled 1GB DDR3 PCIe 2.1 Graphics Card" for $60.  This card is from 2010!  This is actually an ATI GPU - from before AMD bought ATI.  In 2013, I bought an APU - an AMD E-350 that included the motherboard, APU (CPU+ Radeon HD 5450 GPU) in the board for $50 total.  This isn't a deal. It is a very low end GPU.

I'd be weary of buying any GPU used. The ones with the performance you'd want at 2x the budget would likely be abused - used for blockchain mining 24/7 and run very hard. Cheaper versions would be fakes.

That same store has a "PowerColor AMD Radeon RX 6500 XT ITX Overclocked Single Fan 4GB" for $170.  **I don't know if it would fit into that case.** The 6500XT is well reviewed.  That's the next cheapest that isn't another version of the Radeon HD 5450 above.

BTW, that system can't support any GPU over 75W, which limits which GPUs can be used too. I think a PSU upgrade is required and some Dell-specific power cables will be required too.  At some point, an upgrade to a 7 yr old computer makes less and less sense.
[https://www.dell.com/community/Desktops-General-Read-Only/Graphics-card-upgrade-for-dell-optiplex-9020-mini-tower/td-p/5074344](https://www.dell.com/community/Desktops-General-Read-Only/Graphics-card-upgrade-for-dell-optiplex-9020-mini-tower/td-p/5074344) has lots of suggestions for 2016-period solutions.  The case will not accept any full-length GPU and seems to have a 280W PSU, which they say limits the GPU to 75W or less without a PSU upgrade which would allow a GPU up to 150W only. No higher.  They do say that any ITX GPU should fit.

I fear a new GPU is unlikely to make a bit performance difference that wouldn't be easier with a used $80 off-lease computer instead.

If you will run 
"inxi -Fzxx"  and post the output here in forum code tags, we'll be able to see what you have and help you decide if the money is worth it or not.

---

### Post by TheFu on 2022-11-25
Came across this GPU comparison image on reddit today: [http://cdn.mos.cms.futurecdn.net/F4cAJuoNBZrZxoq8oT8VRc.png](http://cdn.mos.cms.futurecdn.net/F4cAJuoNBZrZxoq8oT8VRc.png)  Seemed related, if Tom's Hardware can be trusted.  They are compositing 1080p "medium" settings for the comparison.  So if you game at 1440 or 4K, you'll not believe it or if you game at higher detail settings it will be off too.

---

### Post by Frogs Hair on 2022-11-25
With that budget you could try ebay. A $60.00 budget won't give you many options and driver support is another consideration with older card models. You are likely to find more Nvidia cards than AMD in that price range. I use a 2Gb  Nvidia 730 GT that has driver support, but for how much longer I don't know.

---

