---
title: "Gateway Solo 2500 Sound"
date: 2005-12-11
forum: Multimedia &amp; Video
---

### Post by Taddeusz on 2005-12-11
Hello, new to these forums.  I have a hand-me-down Gateway Solo 2500.  I've gotten this audio to work before on another distro but it's been a while and I'm lost.

I've found that the following command loads the module without errors but I still get no sound:

sudo modprobe opl3sa2 io=0x220 mss_io=0x330 irq=5 dma=0 dma2=1

I've read the entry at wiki.ubuntu.com that says that the sound doesn't work.  I have gotten the sound to work under Mandrake before.  I'm unsure how to load the opl3sa2 module on boot or if it is even possible to get sound from this driver the way Ubuntu is configured?

If anyone can give me any pointers I would be forever greatful.

---

### Post by stuporglue on 2005-12-12
I installed on a Solo 2500 this weekend, and also couldn't get the sound to work with Breezy. 

I upgraded to Dapper (WARNING: Devel version!) and the sound "just worked". I found some posts on a kernel-devel mailing list talking about some fixes for the sound card driver on the Solo; that's what made me upgrade to dapper. 

Did the breezy installer detect the right resolution for your screen? Mine started out at 800x600, but I was able to get it to work correctly at 1204x786...let me know if you need the xorg.conf.

---

### Post by irw on 2006-01-09
I also am trying to resuscitation  one of these laptops, and have found a driver for the sound card, but have yet to make it work.  Perhaps I'll try Draper soon.

Could you let me know how you increased the screen resolution?  I'm stuck at 600x800

Ian.

---

### Post by mediaservant on 2006-01-30
I got an old gatway solo 2500 for free, and also experienced the no-sound problem.  However, some searching on the web found this website:

[http://www.thehayesweb.org/jhayes/solo2500.html](http://www.thehayesweb.org/jhayes/solo2500.html)

And apparently there might be a fix for linux in general, not necessarily for ubuntu.

> Just a note that I found your site while searching for tips on how to get the sound working on my Solo 2500 with Linux 2.4. I had it working previously in 2.2 with certain settings for io, mss_io, irq, dma, and dma2, but these settings did not work 2.4. Through much trial and error, I found that the following seem to work:

io	0x370
mss_io	0x530
irq	5
dma	0
dma2	1


there's other info in the link.

---

### Post by SkyWasher on 2007-08-14
I am using Fiesty on a Gateway Solo 2500.  When I first started using this laptop I had no sound either.  After some digging I found that if your turn off Plug-n-play in the BIOS sound works.   Hit <F2> at startup. 

Then go to the system > peferences > sound  and select Yamaha olp3-sa23 for all the sound settings. 

BTW the module in Fiesty is 'snd-olp3sa2'

good luck

---

