---
title: "VDPAU running on x4 bandwidth - will playback be ok?"
date: 2010-07-20
forum: Multimedia Software
---

### Post by swong on 2010-07-20
I'm considering getting a new motherboard in the future that has a pci-e x16 slot, but the slot only runs at x4 bandwidth.  I will be using a 8800GT, so my question is will the x4 bandwidth have any detrimental performance hit when playing HD videos using VDPAU (H.264 codec)?

---

### Post by cascade9 on 2010-07-20
It should be fine. PCI-e x1 (version 1.x) is 250MB/sec, so a v1.x PCI-e x4 slot should give 1GB/sec bandwidth. 

BTW, why not get a motherboard that supports at least x8 or better yet, x16?

---

### Post by rubylaser on 2010-07-20
Or, if you're thinking of using VDPAU for a HTPC, why not just get one of the new ION 2 based machines like this... Works great with XBMC.
[http://www.newegg.com/Product/Product.aspx?Item=N82E16856173005]("http://www.newegg.com/Product/Product.aspx?Item=N82E16856173005")

---

### Post by swong on 2010-07-20
> **cascade9 said:**
> It should be fine. PCI-e x1 (version 1.x) is 250MB/sec, so a v1.x PCI-e x4 slot should give 1GB/sec bandwidth. 

BTW, why not get a motherboard that supports at least x8 or better yet, x16?

Thanks for the reply.

Ideally, I would like to get a pci-e slot running at the full x16 bandwidth.  Actually I do have a few motherboard choices, the one with the x4 bandwidth is just the cheapest option, so I could spend more to get something better.

---

### Post by swong on 2010-07-20
> **rubylaser said:**
> Or, if you're thinking of using VDPAU for a HTPC, why not just get one of the new ION 2 based machines like this... Works great with XBMC.
[http://www.newegg.com/Product/Product.aspx?Item=N82E16856173005]("http://www.newegg.com/Product/Product.aspx?Item=N82E16856173005")

Thanks for the suggestion.  If I was solely looking at a HTPC, then ION would be good, but I need to use a PC for day-to-day stuff too and the Atom cpu just doesn't cut it for me.

---

### Post by rubylaser on 2010-07-20
Probably the easier way to get a good recommendation is to post what hardware you have (socket, RAM speed, etc), and what's your price range.  Then recommending a motherboard would be much easier.  Can you run a PCI-Express x16 GPU in a x4, yes, but why would you want to, when there are  a multitude of inexpensive motherboards that will allow your card to work as designed.

---

### Post by cascade9 on 2010-07-20
> **swong said:**
> Thanks for the reply.

Ideally, I would like to get a pci-e slot running at the full x16 bandwidth.  Actually I do have a few motherboard choices, the one with the x4 bandwidth is just the cheapest option, so I could spend more to get something better.

I guessed that getting a different motherbaord shouldnt be a problem. Theres got to be a lot of choices at the golden arcade :) 

BTW, what motherboard was it with only a x4 slot? Most of the PCI-e x16 sized slots that dont give full x16 bandwidth are x8, I'm just wondering who did a x4.

---

### Post by swong on 2010-07-20
> **cascade9 said:**
> I guessed that getting a different motherbaord shouldnt be a problem. Theres got to be a lot of choices at the golden arcade :) 

BTW, what motherboard was it with only a x4 slot? Most of the PCI-e x16 sized slots that dont give full x16 bandwidth are x8, I'm just wondering who did a x4.

J&W MINIX 785G, I prefer ITX builds these days.  They are bringing out an 890GX ITX board which supports x16 next month but I'm guessing it's going to be 50% more expensive.

My other option was to get an H55 ITX + Core i3-530 without Nvidia gpu as Intel are working on H.264 hardware decoding on the clarkdale built-in gpus but I don't think that will be ready until Q4 2010.

---

### Post by cascade9 on 2010-07-20
According to the J&W site, its got a 

> 1 x PCI-E x16 Gen.2 slot (support up to x4)

[http://www.jwele.com/motherboard_detail.php?792#_spec](http://www.jwele.com/motherboard_detail.php?792#_spec)

If that means its a PCI-e 2.0 slot (which is what it looks like) then that doubles the bandiwdth from 250MB/sec (per lane) to 500MB/sec (per lane). 2GB/sec bandwidth is far less worrying than 1GB/sec. 

IMO that should be fine, no need to go buying Intel :)

---

