---
title: "Would this be powerful enough to run a MythTV frontend?"
date: 2007-10-07
forum: Multimedia &amp; Video
---

### Post by Scorpuk on 2007-10-07
Processor Intel® Celeron® M Processor 440 (1.86 GHz, 1 MB L2 cache, 533 MHz FSB) 
RAM 1 GB DDR2 SDRAM 667MHz/ 2 GB (max) 
Hard Drive 40 GB serial ATA 
Optical Storage Double-layer DVD+/-RW drive 
Graphics Controller Intel® Graphics Media Accelerator 950GM 
Audio Output Intel® Audio onboard

[link to system]("http://www.transtec.co.uk/GB/E/products/personal_computer/pc/mini_pc.html?mod=prod&name=SY600WCA45-B")


Although I would like to use one of these instead fo the 40Gb HDD:  [4GB Samsung MC4GE04G5APP-0XA 2.5" PATA Solid State HDD]("http://www.scan.co.uk/Products/ProductInfo.asp?WebProductID=643259"), but thats PATA and the m/b is SATA!

---

### Post by jnovinger on 2007-10-08
I sure think so.  My MythTV frontend runs on an AMD Athlon 900, 1 GB of RAM, and a 40GB IDE drive.  It is nothing special, but it plays shows, dvds, music, and mame games just fine.

The thing that saves this box is the nVidia GeForce FX 5200 128mb card.  Again, nothing special, but it takes a load off of the system.

Jason

---

### Post by Scorpuk on 2007-10-08
Thanx for your reply.


I was more concerned over the graphics adapter: Intel® Graphics Media Accelerator 950GM


The system would need to use non vesa drivers to cope with playing live TV and DVD's etc.


I have did a quick search on the 950 and still not 100% sure it would fully work.


Previously I was going to go with a VIA EPIA system, but thats even less supported at the moment with the unichrome drivers. :-(

---

### Post by am_pcguy on 2007-10-08
I've been doing some research, on building a MythTV box.  So I have no practical experience....

That should be fine for DVD's and SD Television.  If you want to record and play HDTV you may want to get a video card that has an MPEG2 decoder built-in.  Most if not all Nvidia 6000 series and up have this.

I'm looking at an ASUS P1-AH2 AMD barebones kit that has an integrated Nvidia 6150.

If you don't care about HD then what you have should be fine as long as your tuner has MPEG2 encoding for SD so you can record.

---

### Post by AusIV4 on 2007-10-08
I had a very comparable system which was used as a MythTV frontend - same processor, same graphics card, same audio, inferior hard drive, half the ram, and it did fine.

Further, when I started using MythTV I had a 750 Mhz AMD processor with 256 MB RAM as a combonation frontend backend. It worked fine for both jobs, so long as it wasn't trying to record and play back at the same time. 

As for your concern for the graphics card, the Intel GMA 950 is nothing to shake a stick at. I wouldn't recommend it for gaming, and it may have a little trouble with HD DVDs, but overall I've found it to be excellent for most Linux uses.

---

### Post by Scorpuk on 2007-10-09
Thanx AusIV4 and am_pcguy.

I may go for this as my frontend then.

My backend has a little more oomph than that so has no trouble recording and currently I have no HD reception so no need for that either.


Master backend server:

Gigabyte GA-G33-DS3R
Intel Q6600
4Gb PC-6400 DDR2
2 x Nova-T 500's
2.2Tb HDD Space (6 x ST3500630AS in RAID 5)

---

### Post by atlfalcons866 on 2007-10-26
you should use JFS as the file system if you use mythtv.

---

### Post by Scorpuk on 2007-10-28
I thought it was XFS, going by theubuntu installation guide?

---

