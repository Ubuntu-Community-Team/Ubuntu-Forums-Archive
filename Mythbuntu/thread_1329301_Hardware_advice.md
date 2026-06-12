---
title: "Hardware advice"
date: 2009-11-17
forum: Mythbuntu
---

### Post by Wipster on 2009-11-17
Hi all,

I have just read the recommended hardware stuff and a few setups for backend+frontend solutions and I wanted to run it past the community before commit to buying if I may. The system will be recording a digital freeview signal with a view to do DVB-T2 when a TV card is released so the rest of the hardware needs to do HD, also want it to be small and quiet and look good as it will be next to my TV. It will also be plugged into my TV with HDMI most likely.

ASUS M3N78-EM                   £53
Athlon 64 X2 6000+              £44
WinTV Nova-TD 500               £60
Kingston (2x1Gb) DDR2 800mhz    £26
Compucase 7K series             £46
WesternDigital 320Gb SATA2 3.5" £32
LG 22xDVD±RW Dual Layer & RAM   £16

Total cost of system £277 
I think the PSU is included in that case (will 200W be enough?) Its a little steep are their any areas that could be cut down in your experiences? Also does Mythbuntu work well with two recorders, is it fine to browse and watch with one and record with the other out of the box?

Thanks for your help and I look forward to getting setup :D

---

### Post by SiHa on 2009-11-17
My only comment would be that you don't appear to have considered cooling. You want a processor that's fairly meagre in it's power requirements, and a fan/heatsink that's quiet (duh!)

1) The Athlon II X2 series have a nominal power rating of 65w as opposed to 89w for the Athlon X2 6000+. Maybe go for a mobo that supports socket AM3, like  [[COLOR="Blue"]_this_[/COLOR]](http://www.dabs.com/products/gigabyte-am3-amd-ddr2-a-gl-5LPS.html) one? I have this running Mythbuntu 9.10 with VDPAU and HDMI audio with very little tweaking (and that only for audio **outside** of Myth).

2)  The stock AMD heatsink/fan is pants. Not terribly efficient, and the fan'll probably die after not too long. The one on my BE lasted about 6 months. I can recommend the Scythe Shuriken heatsink. It's fairly low-profile, and has a 12cm fan. This has the advantage that it is both slow and quiet, and the heatsink hangs over the GPU passive sink, and helps to cool that (runs @62°C playing 1080i). Costs about £28 IIRC.

With this combo, and a 'modified' internal PSU (also has a 12cm fan) I'm hard pushed to hear anything sat right in front of the box, and the TV muted.

On a side-note, I think I saw a post on here yesterday where someone has the Asus mobo you're looking at, and they're struggling with VDPAU. [B]EDIT: Seems it's the frequency-scaling thing, easy enough to sort, so nothing to worry about.
[/B]
As for the rest. 200W should be enough, my frontend draws ~55W, add in a few more watts for a 3.5" (I have 2.5") the optical drive, and a slightly more greedy Athlon and I'd be suprised if it pulled much more than 100-120W, maybe a bit more when the DVD drive's going full pelt.

Cheers

Simon

And yes, it will be able to record one show and watch another with no trouble at all.

---

### Post by cascade9 on 2009-11-17
Watch out for the +6000. Theres 3 different models around, two are 89 watts TDP, the other is a nasty 125 watts. (2 are 3Ghz/2 x 1024k cache, 1 is 3.1Ghz, 2 x 512k...oh and the 125 watt model is 3Ghz, not the 3.1)

Its possibly more CPU than you need, I'd either drop back to a +5200 or +5600, or move up to a AM3 like SiHa suggested. Just to be confusing, theres 3 different +5200s around, two 89 watt, one 65 watts. Get the 65 if you can find one. 

There is also 'black edition' AMD CPUs, they are unlocked for the overclocking crowd. Underclocking is totally possible, and will drop your power requirements and heat. 

Or, and this would be my choice, get an AM3 board, and an Athlon II X2 235e (energy efficient model, 45 watts) I found them in the UK for just a few pounds more than your +6000 for 44 quid-

[http://skinflint.co.uk/a473338.html](http://skinflint.co.uk/a473338.html)

BTW, all 'black edition' CPUs are unlocked, and all the AMD CPUs with a little 'e' on the end are energy efficient models. 

If you do go AM3, think about getting a DDR3 motherboard, not a DDR2. Here, the prices are pretty much the same, and its going to be much easier to source DDR3 later. 

I'm not that sure about the Compucase 7K, but from my quick look its a half-height case. Aka 'right pian in the ****' to get video cards to fit, if you want one later.

---

### Post by Wipster on 2009-11-17
Hi, 
Thankyou both for your replies, your right I didn't consider heating opps :|. I guess I don't want a fan ruining my movie experience :) I notice that the energy efficient models of the CPU are not in stock in the UK at the moment at my usual suppliers, I must be over estimating the power requirements for processing 1080p, those 235e and 240e will be manly enough?
I was considering AM3 to future proof me a bit but the cost of RAM here seems to have doubled recently so it was a bit of a cost saving measure to go the other route, plus I noticed that motherboard featured in a Myth guide proven working :) 

So having a nose about the AM3 DDR3 route I happen across this, ASUS M4A785TD-M, however I know graphics cards are a bit funny with linux and this one has a ATI 4200 series inbuilt, will it be ok for highdef content without kicking off? How is the support for ATI drivers nowadays? I remember them being a right pain (I have Nvidia now on my main).
I did want to try and avoid going down a graphics card route as I wanted to keep this box as small as possible to do the job, the most that will be chucked at it will be 1080p, if it can handle it why over power it :)

Just spotted the Pundit range from ASUS but those are designed for core2, and have Geforce9 series cards in them... nice and small too.

Best regards,
Wip

---

### Post by SiHa on 2009-11-18
> I must be over estimating the power requirements for processing 1080p, those 235e and 240e will be manly enough?
They should be man enought to do it in software, but really, you'd want to offload that to the Graphics Chipset and use VDPAU. You need nVidia 8+ series for this, which both the M3N78-EM and GA-M85M-US2H have on-board. Especially if you don't want the CPU (and hence the CPU cooler)maxed out.

As for ATI, I wouldn't touch them with a bargepole. Speaking from personal experience, Linux support sucks.

---

### Post by cascade9 on 2009-11-18
The 235e and 240e are 2.7/2.8Ghz, compared to a +6000 3/3.1Ghz. A bit less Mhz, but IMO any Mhz drop would be offset by 2Ghz HyperTransport (the +6000 is 1Ghz). I'm sure that the 235e is enough, as I am 99.999% sure I've watched 1080p on my +4800 (2.4 Ghz), 2GB 800Mhz DDR2/8600GT without stuttering. 

AM3 is nice, and probably more future proof, but as far as I know AMD hasnt released any AM3 only CPUs. Currently, all the AM3 CPUs will drop straight into a AM2+ motherboard, and will work in a lot (most?) of the AM2 boards. 

BTW, heres a link for what I've seen as the most common 'minimum requirements' for 1080p, for software decoding- 

[http://www.taranfx.com/blog/1080p-minimum-requirements](http://www.taranfx.com/blog/1080p-minimum-requirements)

2.4Ghz dual core, 600Mhz GPU core, 256MB video RAM. 

If the M4A785TD-M lets you increase sideport RAM from 128MB to 256MB I cant see a problem (its a 700Mhz core). I'm not sure about the current ATI drivers, but from what I've seen around here and the rest of the net, things are getting better for ATI drivers under linux. 

As for the 'pundit' range, well, I think that its prebuild/bare bones boxxen from what I can see. The couple I looked at were SIS/ATI graphics anyway. I think you were thinking of the P5N7A-VM              

[http://www.asus.com/product.aspx?P_ID=8YiUFvK51IergAqY&templete=2](http://www.asus.com/product.aspx?P_ID=8YiUFvK51IergAqY&templete=2)

GF 9300 GPU, and a 450Mhz core. So it might be a little bit slow, but to be honest, I dont know enough about nVidia PureVideo HD (VP2) to know if it will play 1080p without stuttering. I guess it would. I also am not sure how low you can go with ATIs Unified Video Decoder (UVD).

---

### Post by concordfta on 2009-11-18
Your ASUS motherboard has the nVidia 8300 graphics on-board.  The 8300  has VDPAU Feature Set B support which has complete support for MPEG2, H264 and VC1.  Your HD will be completely off-loaded to the GPU.

There are guys here that are running OTA HD and H264 HD (1080p) on the Intel Atom cpus with nVidia ION graphics chips (nVidia 9400)

I can run full 1080HD H264 mkv on my Atom board using mplayer or mythtv with ONE cpu going to around 8% usage (mythtv) and 2% usage (mplayer).  I have the 330 atom which is 1.6ghz...

Something to think about...

[ftp://download.nvidia.com/XFree86/Linux-x86/190.42/README/appendix-a.html](ftp://download.nvidia.com/XFree86/Linux-x86/190.42/README/appendix-a.html)
[ftp://download.nvidia.com/XFree86/Linux-x86/190.42/README/appendix-h.html#vdpau-implementation-limits-decoder](ftp://download.nvidia.com/XFree86/Linux-x86/190.42/README/appendix-h.html#vdpau-implementation-limits-decoder)

---

### Post by cascade9 on 2009-11-20
Thanks for a better idea of how much CPU power you need if your running VDPAU. 

Based on that, I guess that a 'black edition' downclocked to, say, 1.0/1.6Ghz or so would give you plenty of power for running 1080p, and give you a very cool CPU, even with a stock cooler. 

I just wish my old GF6600GT  supported VDPAU, then I could try my old 1.2Ghz Athlon (266mhz FSB, 'C' model) as a mythTV box. Oh well.

---

### Post by LorenzoS on 2009-11-20
The tests and user forums on silentpcreview.com is _very_ helpful in finding the right balance between performance and noise for your application.  I haven't been there much since my last build 2 years ago but I would spend some time there before selecting any new hardware.

---

