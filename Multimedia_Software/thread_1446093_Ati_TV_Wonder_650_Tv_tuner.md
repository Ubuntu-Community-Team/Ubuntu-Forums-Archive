---
title: "Ati TV Wonder 650 Tv tuner"
date: 2010-04-03
forum: Multimedia Software
---

### Post by Lucky75 on 2010-04-03
Does anyone know of any way to get this thing to work on Karmic? Just to be able to watch TV, not even to record? I can't seem to get it to recognize it.

lsusb just shows:
```
 Bus 001 Device 006: ID 0438:b003 Advanced Micro Devices, Inc. 
```

but it doesn't show up in dev/video0 or anything like that, and I don't know of a program which will play it. I don't really have the money to go out and buy another tv tuner, so I really would like to get this one to work, or else I'm going to have to switch to windows :S

Thanks!

---

### Post by lidex on 2010-04-03
You want the good news or the bad news first? OK, let's start with the bad news: there is no good news! 
[Unsupported]("http://www.linuxtv.org/wiki/index.php/ATI/AMD_TV_Wonder_650_PCI")
[ATI's TV Wonder 650 Recall]("http://news.softpedia.com/news/ATI-s-TV-Wonder-650-Recall-34108.shtml")

---

### Post by Lucky75 on 2010-04-03
Hmm, this is the USB version, and it's Diamond brand, although not too sure if that makes a difference. It's relatively new (but not new enough to return), so I don't think it would be affected by a recall from 4 years ago.

I noticed that the TV wonder 600 USB *should* be supported. Can I use that? Is there any way to get at least basic video support for it? Who is responsible for the drivers anyway? 

Thanks!

---

### Post by lidex on 2010-04-03
In all the threads I saw, not one person was able to get it working (the 650). Your best bet is to get a card with hardware encoding. What do you need - QAM, ATSC, DVB-S, DVB-T? Have a look here:
[http://www.linuxtv.org/wiki/index.php/Main_Page]("http://www.linuxtv.org/wiki/index.php/Main_Page")

Here for Hauppage, they are well supported:
[http://www.mythtv.org/wiki/Hauppauge_PVR_Card_Matrix]("http://www.mythtv.org/wiki/Hauppauge_PVR_Card_Matrix")

---

### Post by Lucky75 on 2010-04-04
Its ridiculous to pay for another card just because linux can't support it. I don't really have the money to purchase another one, unfortunately :(

---

### Post by lidex on 2010-04-04
So dual-boot.

---

### Post by Lucky75 on 2010-04-04
> **lidex said:**
> So dual-boot.

The whole point of a tv tuner is to be able to watch TV on screen while doing work. Rebooting sort of defeats its purpose :)

Who writes new drivers for this sort of thing? Is there any place I can request an eventual driver or something?

There's no way of somewhat adapting the 600 driver to work? It seems to recognize the device OK...

Thanks!

---

### Post by Lucky75 on 2010-04-04
bump

---

### Post by Lucky75 on 2010-04-04
bump

---

### Post by Mark Phelps on 2010-04-05
Please don't keep bumping this post because you're apparently unhappy with the answers you got. You saw the post on the card recall.  You could try contacting AMD/ATI -- but since they have dropped support for LOTS of cards, they are unlikely to be sympathetic.

Suggest you wait until 10.04 is released (there are major problems with the ATI drivers in it right now), and when that happens, burn a LiveCD, boot from it, and see it the new open source drivers help any.

You can also, in the interim, go to the Phoronix forums, do a search on your card model, and see if there are any threads there dealing with it.  They do a LOT of work testing and configuring ATI cards & drivers.

---

