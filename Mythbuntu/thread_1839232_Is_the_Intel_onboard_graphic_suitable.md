---
title: "Is the Intel onboard graphic suitable?"
date: 2011-09-05
forum: Mythbuntu
---

### Post by lmclaren on 2011-09-05
Hi,

I was thinking of buying this for a combined FE/BE.

The TV is only standard def but may go to high def in the future.

Do you think the onboard graphics on this board would be suitable or do I need to buy an Nvidia?

[http://www.pccasegear.com/index.php?main_page=product_info&cPath=138_711_1183&products_id=17618](http://www.pccasegear.com/index.php?main_page=product_info&cPath=138_711_1183&products_id=17618)

[http://www.gigabyte.com/products/product-page.aspx?pid=3856#ov](http://www.gigabyte.com/products/product-page.aspx?pid=3856#ov)

thanks

Lee

---

### Post by wirepuller134 on 2011-09-05
I can't tell you exactly, but I can list what we have used to push SD content in the past.
  Acer rivo 3600 with Nvidia ion graphics, Nvidia 5500 agp, an Intel P4 motherboard with built in graphics, Intel P2 motherboard with 815 graphics.  
  We are using 4 Acer rivo's and 1 Intel G41 now for our front ends.  All using on board graphics.  They are small, quiet, and efficient.

---

### Post by can2002 on 2011-09-05
Hi there,

I have a couple of 'fixed' frontends that I'm using for a mixture of SD and HD content; one is an ION-based compact Net-top and the other is a compact desktop PC with an nVidia GT240 card.  They are both rock-solid for HD playback.

I also have a 2-3 year-old laptop with an Intel Core-2 Duo processor with a built in Intel GMA X3100 controller.  It is absolutely fine for SD and OK-ish with HD.  I would have thought the in-built controller of the board you've listed would be superior to my in-built graphics, so it should be OK.

I can't see for sure whether the integrated HDMI output will work with Audio too, Is this something you've thought about?  The expansion slots seem to open up the possibility to go with a nVidia card in the future, so you'd always have the option of adding later...

Cheers,
Chris

---

### Post by lmclaren on 2011-09-05
Thanks for the feedback

Lee

---

### Post by tobiz on 2011-09-06
> **lmclaren said:**
> Hi,

I was thinking of buying this for a combined FE/BE.

The TV is only standard def but may go to high def in the future.

Do you think the onboard graphics on this board would be suitable or do I need to buy an Nvidia?

[http://www.pccasegear.com/index.php?main_page=product_info&cPath=138_711_1183&products_id=17618](http://www.pccasegear.com/index.php?main_page=product_info&cPath=138_711_1183&products_id=17618)

[http://www.gigabyte.com/products/product-page.aspx?pid=3856#ov](http://www.gigabyte.com/products/product-page.aspx?pid=3856#ov)

thanks

Lee
I'm running an Intel Atom 525 1.6GHz with the Intel graphics chip. This is ok for SD TV but not HD TV using VLC.  Digital TV doesn't make to many demands on a CPU when recording, it's playback that's the problem.  I've found Nvidia pretty good for graphics support. My main MythTV production system (see signature) has an Nvidia on-board GPU and with the CPU is good for SD & HD TV without using VDPAU but HD goes to ~80% processor; VDPAU should reduce this a lot but this is not supported on Intel only Nvidia.

---

### Post by gunksta on 2011-09-06
I've got a i5 2520 on my laptop and it runs brilliantly. I have attached it to my HD television and watched movies on it without a problem. Output looks very good. The new Intel stuff isn't ready for the video-game market, but for those of us who really just want to watch movies and play a little chess, it works brilliantly and is fairly energy efficient.

---

### Post by David Grigor on 2011-09-06
It should do just fine providing you have enough cpu power since there will no hardware acceleration. Likely any dual core would be sufficient.  HDMI w/ sound may or may not be an issue to get working. That would be the only wildcard.

Worst case try the onboard first, if doesn't work well enough you can always add the video card later. The longer you wait usually the cheaper they get so doesn't hurt to wait.

---

### Post by lmclaren on 2011-09-06
Thanks for the feedback, I am putting in the top of the I5 range processor, will know for sure by the weekend. :)

---

