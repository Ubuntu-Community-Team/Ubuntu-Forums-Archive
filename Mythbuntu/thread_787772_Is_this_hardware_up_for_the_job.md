---
title: "Is this hardware up for the job"
date: 2008-05-09
forum: Mythbuntu
---

### Post by tedius on 2008-05-09
I'm about to build myself a MythTV setup, and would like some advice about the hardware.

I going to be doing this in two phases.  Phase 1 build a backend system and phase 2 build the front end system.  At the moment I'm only interested in phase 1 as my PC will allow me to get every thing setup before I go looking for a front end.

This is what I have in mind for the backend:
Case: [Antec NSK1380 UK]("http://www.antec.com/uk/productDetails.php?ProdID=00136")
Motherboard/CPU: [VIA iDOT PC2500E PC-1 Mainboard - 1.5Ghz C7-D]("http://linitx.com/viewproduct.php?prodid=11878")
Memory: 1GB of DDR2 ram
Harddisk: 250Gb SATA drive
TV card: [Hauppauge Digital: WinTV-Nova-T 500]("http://www.hauppauge.co.uk/pages/products/data_novat500.html")

Would this be sufficient for a backend system?

Any comment would be welcome.
Thanks

---

### Post by hencke on 2008-06-03
Here are a few possibly useful links:

[LIST=1]
[*][http://en.wikipedia.org/wiki/FlexATX](http://en.wikipedia.org/wiki/FlexATX)
[*][http://www.linuxtv.org/wiki/index.php/DVB-T_PCI_Cards#Hauppage](http://www.linuxtv.org/wiki/index.php/DVB-T_PCI_Cards#Hauppage)
[*][http://www.mythtv.org/docs/mythtv-HOWTO-3.html#ss3.1](http://www.mythtv.org/docs/mythtv-HOWTO-3.html#ss3.1)
[/LIST]

From (1) I'd say the motherboard fits in the Antec case properly. The case power supply is more than adequate for your setup. Although the C7 isn't a very powerful processor, I think it should be up to the job, judging from (3). Remember that with that processor you probably can't change this to be a combined backend-frontend, but that's not what you want to do anyway. The amount of RAM is more than adequate. The 250 GB drive should give you hundreds of hours of recordings, depending on the bitrate. Also (2) seems to suggest the Hauppauge card works with linux.

The only thing I would be concerned with is whether or not the processor is up to the task. Please post back, I'm also interested in how it goes.


> **tedius said:**
> I'm about to build myself a MythTV setup, and would like some advice about the hardware.

I going to be doing this in two phases.  Phase 1 build a backend system and phase 2 build the front end system.  At the moment I'm only interested in phase 1 as my PC will allow me to get every thing setup before I go looking for a front end.

This is what I have in mind for the backend:
Case: [Antec NSK1380 UK]("http://www.antec.com/uk/productDetails.php?ProdID=00136")
Motherboard/CPU: [VIA iDOT PC2500E PC-1 Mainboard - 1.5Ghz C7-D]("http://linitx.com/viewproduct.php?prodid=11878")
Memory: 1GB of DDR2 ram
Harddisk: 250Gb SATA drive
TV card: [Hauppauge Digital: WinTV-Nova-T 500]("http://www.hauppauge.co.uk/pages/products/data_novat500.html")

Would this be sufficient for a backend system?

Any comment would be welcome.
Thanks

---

### Post by blackoper on 2008-06-03
well since I have that board I'll comment on it. It would be really slow for commercial detection but would eventually get it done (sd content only). Also the nic is 100mbit but that should easily support two frontend clients for sd content and even hd. If you want to use this backend for hd content, commercial detection wouldn't really be an option but it should be able to serve the content to the frontends ok. I use mine as a slave backend only and to control a touchscreen in my home

---

