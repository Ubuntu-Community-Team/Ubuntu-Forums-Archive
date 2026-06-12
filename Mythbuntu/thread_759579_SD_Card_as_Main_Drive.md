---
title: "SD Card as Main Drive"
date: 2008-04-19
forum: Mythbuntu
---

### Post by moeFinley on 2008-04-19
The hard drive in my Shuttle media PC has got old and loud so I was going to replace it with a 16GB SD card and install Mythbuntu (currently just vanilla Ubuntu with Kaffeine).

All my media would be on external hard drives but is 16GB enough for the system?  Can I put the 'backend' on the external drives?

Thanks for any advice

---

### Post by ille on 2008-04-19
16G is alot if used only for the system.  3GB is enough. 

You meen "can I put the media" on the external drive", yes, change the recording dir to the path of the external drive.

---

### Post by volkswagner on 2008-04-19
How is your SD card connected?  Is it on an USB header? If so it would be the same as an external drive.   Won't the SD card be poor performance?  What are the read/write speeds, and buffer?

I agree a 4gig card would be large enough for the system.

---

### Post by ille on 2008-04-20
I've seen a PATA (IDE) to Compact Flash adapter for using the CF card as a IDE drive. Kinda cool since the bios does not need to be able to boot over USB.

---

### Post by ian dobson on 2008-04-20
Hi,

Why not just use a 2 1/2 inch portable harddisk.

Flash drives have a limited number of writes. I ran a small linux from a CF card and after about 6 months I started having write errors.

Regards
Ian Dobson

---

### Post by mrand on 2008-04-20
> **ian dobson said:**
> Hi,

Why not just use a 2 1/2 inch portable harddisk.

Flash drives have a limited number of writes. I ran a small linux from a CF card and after about 6 months I started having write errors.

Regards
Ian Dobson

Depends on a lot of things.  Wear leveling algorithms help tremendously, as does using the latest generation flash chips which have millions of writes (I forget what they are up to now... maybe 10's or 100's of millions of writes).

Have fun,

  Marc

---

### Post by superm1 on 2008-04-21
Something else you can consider is moving the backend functionality off elsewhere on your network.  You can then do a diskless boot (which is included in 8.04) on this box and still be able to do everything you could previously.

---

### Post by turlian on 2008-04-24
As another data point, I built a picture frame out of an old laptop, and it runs Damn Small Linux off of a 1GB CF in an IDE adapter.  Totally silent, as it never even needs the fans.  Granted, I underclocked it...

It's been running for about a year now with no write errors, even after wirelessly updating with new pics hourly.  I even messed up my crontab, so this thing is running 24x7.

Point is that you could probably have a frontend run great off of flash memory.

---

### Post by moeFinley on 2008-04-26
Thanks for the advice guys.  I'm going to install Mythbuntu on to the hard drive today just to test it out.

I was going to buy a SD to IDE adapter, would CF be better?

I didn't know about the limit writes thing!  You would think they would have to mention it when you buy these things.

---

### Post by Jolidog on 2008-04-27
I'm going to try something similar, but I'm going to use a CF to SATA adapter that supports UDMA. There are CF cards capable of million of writes, and speeds of 40MB read/write like the Sans disk Extreme IV line.
Even with million of writes my plan is to disable swap, only relying on the 4Gb RAM.

Media will be handled by a RAID controller, so the CF would be only for the system.

I'm still trying to decide if I get a 4Gb or a 8Gb CF Card.

Also I'm trying to find out what log files can be disabled in the system. After the installation is complete I don't think there will be many writes to the card.

I'll let you know how it goes, I'm still expecting the components to arrive.

---

### Post by turlian on 2008-04-28
> **moeFinley said:**
> 
I was going to buy a SD to IDE adapter, would CF be better?



My personal preference is for CF, since they already speak IDE (technically, ATA-4).  The adapter you use is more of a pin converter rather than something that has to actually do a translation (like SD to IDE would).

You can even find CF/IDE adapters that plug directly into your motherboard.  No cable needed.  

[http://www.psism.com/adcf.htm]("http://www.psism.com/adcf.htm")

---

