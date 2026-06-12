---
title: "Zotac Zbox AD03/ID33 for frontend and backend?"
date: 2011-04-20
forum: Mythbuntu
---

### Post by Koppschaechter on 2011-04-20
I find the[[COLOR=blue]Zotac Zbox Blu-ray **AD03**[/COLOR]]("http://pden.zotac.com/index.php?page=shop.product_details&flypage=flypage_images.tpl&product_id=309&category_id=127&option=com_virtuemart&Itemid=1") and the [[COLOR=blue]Zbox Blu-ray HD-**ID33**[/COLOR] ]("http://pden.zotac.com/index.php?page=shop.product_details&flypage=flypage_images.tpl&product_id=277&category_id=127&option=com_virtuemart&Itemid=1")quite interesting. But I'm not sure if they will work the way i want them to. I'm especially curious about the AD03 with the AMD Fusion Chipset. Will Mythbuntu support the Hardware decoding with this chipset? I know it generally works with Atom + ION (ID33).
 
I'm not sure if those boxes will be able to handel both, frontend and backend, can someone please help me about that?
 
If it is able to handle both, can it run an webserver parallel to that, too? And maybe a few other server applications (for example a wiki)?
 
I searched and googled for a while, but could not really find answers to those questions.

---

### Post by ian dobson on 2011-04-20
Hi,

The boxes look quite interesting. An atom should be enough for a backend or frontend (if hardware acceleration works) but if you have both on the same box, maybe you need to reduce the CPU usage of the backend by not transcoding or commflagging which recording/playback.

Note the box uses an AMD/ATI graphic card and they're usually abit problamatic under linux, especially with MythTV/Video playback. I think ATI support the vaapi interface for video acceleration, and I think there are patches for MythTV floating about, but I'm not sure what mythbuntu supports.

EDIT: Have a look here [http://www.mythtv.org/wiki/Choosing_Frontend_Hardware](http://www.mythtv.org/wiki/Choosing_Frontend_Hardware) at the bottom of the page.
Regards
Ian Dobson

---

### Post by nickrout on 2011-04-21
the answer is 'no':  video acceleration will not work on the AD03 machine with mythtv. It should with the 133 as it is stated to be ion2.

I am not sure that you will be able to play bluray disks either.

---

### Post by Koppschaechter on 2011-06-27
I still can't find any statements on the web whether the Atom/Ion Zbox ID33 can handle both front- and backend at the same time whith having enough ressources left to also run a webserver and a wiki and probably some other "small" server applications.

Any news on that topic?

---

### Post by nickrout on 2011-06-27
How long is a piece of string?

How many streams are you wanting to record at once? How many are you wanting to commflag and/or transcode? Is this HD or SD? What other services do you wish to run.

Frankly i wouldn't want to run a combined BE/FE again anyway. Get yourself a decent machine for a backend/server and use the ion board for a nice quiet frontend.

---

### Post by ZedThou on 2011-06-28
I have an IONITX-A (Atom 330) combined front/backend, with 4GB RAM, a couple of 5400 rpm laptop drives and an HDHomeRun. I overclock it a bit, works great. Records and commflags four HD programs at a time while also playing back, all without a hiccup. Transcoding is another matter, very slow obviously. I've had to do a few contortions with mythexport to find a viable solution for archiving. The only web serving I do is with mythweb and it runs fine. All in all, I love this quiet little box. It also lets me incorporate hundreds of gigabytes of FLAC-encoded music into the entertainment center and the boxes of CDs can be stored in the basement.

So I think the HD-ID33 would work just fine, although I'd want another disk.

---

### Post by Jompa on 2011-08-03
What about the [ZBOX AD02?]("http://pden.zotac.com/index.php?page=shop.product_details&flypage=flypage_images.tpl&product_id=334&category_id=75&keyword=ad02&option=com_virtuemart&Itemid=1") Would that work as a mythbox?

---

### Post by ZedThou on 2011-08-03
> **Jompa said:**
> What about the [ZBOX AD02?]("http://pden.zotac.com/index.php?page=shop.product_details&flypage=flypage_images.tpl&product_id=334&category_id=75&keyword=ad02&option=com_virtuemart&Itemid=1") Would that work as a mythbox?

The AD02 and AD03 are the same platform, so I suppose the answer is unfortunately no.

---

### Post by Jompa on 2011-08-04
Bummer, it looks very nice.

---

