---
title: "Motherboards: help me understand my choices"
date: 2008-08-30
forum: Mythbuntu
---

### Post by Sixten on 2008-08-30
I'm considering replacing a very aged Myth box with a new, from-scratch build, and I need some help sifting through the piles of advice.

I'm mostly interested in an HTPC to record and time-shift ATSC broadcasts (no cable, satellite, or analog broadcast) and watch ripped content (XViD, H.264, etc.). Maybe someday (when they're cheaper) will get a Blu-Ray drive. Will be hooked up to a 720p LCD TV, so I'm not super-concerned about 1080p playback.

It seems like the integrated graphics are really, really good these days, but I'm not sure how the Linux driver support is. It'd be nice not to need another card, but not if I'm stuck in driver hell.

I've read some very, very positive things about the new 780G motherboards for AMD (like [this one]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813128090")). The main worry I have there is that those reviews are mostly Windows-centric; the conventional wisdom for MythTV boxes has always been, "go with NVIDIA." On the other hand, it seems like the main benefits of that (driver quality, hardware acceleration support) are very much diminished these days.

There are a number of motherboards with NVIDIA graphics (6100, 7050, 8200) for both AMD and Intel, and also Intel options with their integrated graphics. Would any of those provide a significant advantage in speed, quality, or driver support over the 780G options?

---

### Post by SniperKIng on 2008-08-31
I too wish to know about this.As i too am lookin to buy a new board to see if my current one is faulty.im lookin for one with 7.1 surround sound with built in graphics not being much of a worry as i have an Nvidia 8400GS. Reading around i have seen posts reguarding linux and its compatabillity with the new nvidia 8200 onboard chip set being pretty poor but mayby this has changed now.

That board has taken my fancy

 [http://www.asus.com/products.aspx?l1=3&l2=149&l3=676&l4=0&model=2181&modelmenu=1](http://www.asus.com/products.aspx?l1=3&l2=149&l3=676&l4=0&model=2181&modelmenu=1)

Whould it be a good choice?

---

### Post by Lindsay.Mathieson on 2008-08-31
> **Sixten said:**
> There are a number of motherboards with NVIDIA graphics (6100, 7050, 8200) for both AMD and Intel, and also Intel options with their integrated graphics. Would any of those provide a significant advantage in speed, quality, or driver support over the 780G options?

I'd say any of those would be better than a 780G, from what I've seen on the forums and mailing list the ATI drivers are still a world of grief for video playback. ATI do seem committed to improving it - Maybe in a years time when the opensource drivers have had time to shake out.

I have a Asus M2N-DVI with Onboard 7050 and its been excellent. With a AMD 5200+ its been doing HD (720p) via DVI with no problems.

---

### Post by Sixten on 2008-08-31
> **Lindsay.Mathieson said:**
> I have a Asus M2N-DVI with Onboard 7050 and its been excellent. With a AMD 5200+ its been doing HD (720p) via DVI with no problems.
If you were to build a new machine from scratch, would you choose the same thing? Or would you go for something different now?

---

### Post by Lindsay.Mathieson on 2008-08-31
> **Sixten said:**
> If you were to build a new machine from scratch, would you choose the same thing? Or would you go for something different now?

I would like to try the 780G because the promise looks so good. But not for the production media box my wife will be using :) Probably my next personal Desktop M/B will be a 780G which I can play with to my hearts content.

But the PC in the living room - much more conservative with that, downtime is *not* an option so cutting edge is not desirable. I know the 7050 works well.

I'd probably go for HDMI output rather than DVI, just so I could try SPDIF output via HDMI. There is a M2N-HDMI board which I has a 8300 Chipset (I think). But otherwise yeah the same. The Onboard Audio is a ALC663 which support 5.1 surround sound, that did take some manual tweaking but its working now.

However it is analog audio out - SPDIF is a add on. What sort of sound output are you looking for?

---

### Post by Sixten on 2008-08-31
> **Lindsay.Mathieson said:**
> However it is analog audio out - SPDIF is a add on. What sort of sound output are you looking for?
I'd be thrilled if I could just do audio and video over HDMI. There's no amp / audio system; I'd just be connecting the computer to the TV. If I could use HDMI, then it'd just be one cable: no adapters, no fuss.

The reading I've been doing suggests that, once again, the reality may lag a little behind the dream, in Linux.

---

### Post by Lindsay.Mathieson on 2008-09-01
> **Sixten said:**
> I'd be thrilled if I could just do audio and video over HDMI. There's no amp / audio system; I'd just be connecting the computer to the TV. If I could use HDMI, then it'd just be one cable: no adapters, no fuss.

What inputs does your TV have? Most modern TV's have a stereo input for a simple cable from the PC to the TV. That was what I was doing originally with mine - DVI-HDMI for video and a simple 3.5mm-RCA cable for audio.

---

### Post by Sixten on 2008-09-01
> **Lindsay.Mathieson said:**
> What inputs does your TV have? Most modern TV's have a stereo input for a simple cable from the PC to the TV. That was what I was doing originally with mine - DVI-HDMI for video and a simple 3.5mm-RCA cable for audio.
The same setup would work. There's a pair of inputs that has an HDMI paired with a set of RCA jacks for audio. But that's two cables, both of which need to be converter cables, and/or use adapters. It's not *such* a big thing, but it just seems silly to have a single connector available, and not be able to use it.

That's very much secondary, however, to the issue of choosing a board that isn't going to be all kinds of problems in more significant areas (like the hell of video drivers).

---

### Post by Sixten on 2008-09-03
After doing some more reading on the Intel options (after reading lots of support for their stuff), it sounds like the G45 boards would pretty much exactly fill the niche I'm looking for, such as the [ASUS P5Q-EM]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813131336").

The biggest issue I've seen seems to be their comparative novelty. They haven't been out long, and there aren't that many choices yet (and none < $100). Until 8.10 lands, the graphics support won't really be there in the official packages; I'd have to compile all of that myself (which doesn't sound like much fun). On the other hand, I can't see myself pulling the trigger on buying this stuff for another month, anyway.

Does anyone have experience with that chipset yet, or have strong reasons why I'd want to stick to something older (like the [G31]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813131288"), or P35 + discrete graphics)?

---

### Post by fusionisthefuture on 2008-09-09
i agree with you that the G45 chipset on that asus board sounds like the perfect HTPC setup, but youre also right about the lack of support right now in linux.  if youre willing to wait, i would, i think im going to, because this chipset has built in hardware acceleration of hd codecs (with the right programming, of course), which i dont think any previous chipsets did.  i really like the idea of underclocking my cpu and having the video card do most of the work.  

ive heard that the g35 is incredibly stable and well supported in linux, and its not like you wouldnt be able to decode hd, its just that you wouldnt get much help from your video card, and your processor would be doing most of the work.  

also, if youve made up your mind and decided to wait, i think the asus board is quite a bit better than its intel counterpart, albeit at about $20 more expensive.  its got some neat HTPC features like wake on usb (which i think you could use to make an IR remote with usb reciever wake the computer), wake on lan, and my favorite, wake on real time clock, which makes it automatically boot at a certain time every day.

one thing i will warn people of is anything ATI.  i have two ati cards in two different computers, one old and one new, and both of them have tried to run mythtv.  both of them make everyone look like smurfs.  their faces are blue.  the desktop looks fine, everything does, until you try to use the cards for video playback, then youre kicking your *** for buying ATI.  ive never used intel, but i have used nvidia, which didnt come without its problems.  from what i understand, driver support in linux goes like this: Intel, Nvidia, ATI.  intel is the only one that allows fully open source drivers, nvidia and ati release their own, but ati is really, really bad at it.

---

