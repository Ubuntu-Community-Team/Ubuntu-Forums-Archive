---
title: "New build spec - advice needed!"
date: 2011-07-23
forum: Mythbuntu
---

### Post by Alistair1234 on 2011-07-23
Hello,

Firstly, I have not built a pc before but fancy having a go at a HTPC running mythbuntu. After much research, I have come up with the set-up below. Can someone have a look through the spec and tell me if I have screwed up anywhere or if there are better alternatives to anything listed. I want the machine to watch/record freeview tv (and upgrade to dvb-t2 for HD in the future), rip/encode/archive my DVD collection (I can leave this overnight so speed is not my biggest concern) with the possibility to upgrade this capability to blu-ray in the future.

I also need some advice on the PSU - how much power will I need and what is the quietest way of getting it?

Intel Pentium G840 2.8GHz Socket 1155 3MB L3 Cache Retail Boxed Processor 
Gigabyte GA-HA65M-D2H-B3 H61 Socket 1155 8 Channel Audio mATX Motherboard
Fractal Design Define Mini Case
Hauppauge WinTV Nova-TD 500 Dual digital DVB-T PCI Freeview TV Tuner
Asus GeForce G210 SILENT 512MB DDR2 DVI VGA HDMI Out DirectX 10.1 Low Profile PCI-E Graphics Card
Hitachi Deskstar 1TB Hard Drive SATAII 7200rpm 32MB Cache - OEM
Crucial 4GB (2x2GB) DDR3 1333MHz/PC3-10600 Memory Kit CL9 1.5V
Pioneer DVRS19LBK 24x DVD±RW DL & RAM with Labelflash SATA

Total cost w/o PSU = £400

I fully intend to upgrade the cooling/fans etc over time to gradually quieten this system down, but is this lot suitable to get me up and running?

If there is anywhere where I could save a chunk of cash because I have gone overboard then shout up!

---

### Post by aquarius18 on 2011-07-24
> **Alistair1234 said:**
> Hello,

Firstly, I have not built a pc before but fancy having a go at a HTPC running mythbuntu. After much research, I have come up with the set-up below. Can someone have a look through the spec and tell me if I have screwed up anywhere or if there are better alternatives to anything listed. I want the machine to watch/record freeview tv (and upgrade to dvb-t2 for HD in the future), rip/encode/archive my DVD collection (I can leave this overnight so speed is not my biggest concern) with the possibility to upgrade this capability to blu-ray in the future.

I also need some advice on the PSU - how much power will I need and what is the quietest way of getting it?

Intel Pentium G840 2.8GHz Socket 1155 3MB L3 Cache Retail Boxed Processor 
Gigabyte GA-HA65M-D2H-B3 H61 Socket 1155 8 Channel Audio mATX Motherboard
Fractal Design Define Mini Case
Hauppauge WinTV Nova-TD 500 Dual digital DVB-T PCI Freeview TV Tuner
Asus GeForce G210 SILENT 512MB DDR2 DVI VGA HDMI Out DirectX 10.1 Low Profile PCI-E Graphics Card
Hitachi Deskstar 1TB Hard Drive SATAII 7200rpm 32MB Cache - OEM
Crucial 4GB (2x2GB) DDR3 1333MHz/PC3-10600 Memory Kit CL9 1.5V
Pioneer DVRS19LBK 24x DVD±RW DL & RAM with Labelflash SATA

Total cost w/o PSU = £400

I fully intend to upgrade the cooling/fans etc over time to gradually quieten this system down, but is this lot suitable to get me up and running?

If there is anywhere where I could save a chunk of cash because I have gone overboard then shout up!

That plan looks very similar to what I have in mind. Don't think that you have gone OTT. 

You could possibly save a few cents (pence in your neck of the woods) by shopping around. Wouldn't even discard ebay for some of the stuff such as your graphics card.

---

### Post by itlarson on 2011-07-24
My only comments are I would go with a full size motherboard, and a 2tb hard-drive.  At least if you are planning to record high-def, and have multiple internal tuners, like I do.  

 I have a similar video card, and it works fine with the "advanced" vdpau de-interlace, as long as I follow the advice in the troubleshooting section of [this]("http://www.mythtv.org/wiki/VDPAU") wiki.  Be sure the card has enough airflow.  Mine was shooting up to 90c until I added another fan to my case.  

If you are running a all-in-one system in your living-room, like I am, you will want to be carefull what hardware you choose.  At 65w, your CPU should run cool enough, but you'll probably want different heat-sink for it.  You'll also need a quiet 120mm fan PSU, and lots of large 800rpm fans.  Personally I would sacrifice some hard-drive speed for less noise and power consumption.  In my system I am running a 2tb raid 1 using two Samsung EcoGreen drives, and their seek noise is inaudible.  The Hitachi Deskstar 5K3000 is also supposed to be very quiet, as are Western Digital green drives, which I have used in the past.  The best reference for computer noise always used to be  [SilentPCreview]("http://www.silentpcreview.com"), but unfortunately they don't test equipment much any-more.  Their forums are still active, though.

---

### Post by AlecJ on 2011-07-25
> **Alistair1234 said:**
> Hello,

Firstly, I have not built a pc before but fancy having a go at a HTPC running mythbuntu. After much research, I have come up with the set-up below. Can someone have a look through the spec and tell me if I have screwed up anywhere or if there are better alternatives to anything listed. I want the machine to watch/record freeview tv (and upgrade to dvb-t2 for HD in the future), rip/encode/archive my DVD collection (I can leave this overnight so speed is not my biggest concern) with the possibility to upgrade this capability to blu-ray in the future.

I also need some advice on the PSU - how much power will I need and what is the quietest way of getting it?

Intel Pentium G840 2.8GHz Socket 1155 3MB L3 Cache Retail Boxed Processor 
Gigabyte GA-HA65M-D2H-B3 H61 Socket 1155 8 Channel Audio mATX Motherboard
Fractal Design Define Mini Case
Hauppauge WinTV Nova-TD 500 Dual digital DVB-T PCI Freeview TV Tuner
Asus GeForce G210 SILENT 512MB DDR2 DVI VGA HDMI Out DirectX 10.1 Low Profile PCI-E Graphics Card
Hitachi Deskstar 1TB Hard Drive SATAII 7200rpm 32MB Cache - OEM
Crucial 4GB (2x2GB) DDR3 1333MHz/PC3-10600 Memory Kit CL9 1.5V
Pioneer DVRS19LBK 24x DVD±RW DL & RAM with Labelflash SATA

Total cost w/o PSU = £400

I fully intend to upgrade the cooling/fans etc over time to gradually quieten this system down, but is this lot suitable to get me up and running?

If there is anywhere where I could save a chunk of cash because I have gone overboard then shout up!

Your not over the top, I've ended up with 4Tb in storage, I run Myth from a 400Gb drive and use the bigger drives for storage of TV,music, dvds and music, no more dvd's or cd's in the lounge.
The case you spec is too small, the main problem is heat, used to cause no end of crashes.
I now use a rack type case which is large enough for the drives 700w power supply silent cpu cooler and silent case fans. I removed the handles and the sliders from the case and the lockable front flap is great for keeping kids out.
It is a larger black box under the telly, but of course you won't need the old cd player HiFi or DVD or indeed a VCR, old laptops using CF memory cards for hard drives can be great on wifi around the house as long as you have enough TV cards?

I have my old Nova T for sale if you want as I moved to 4 PCI dvb-s cards from the old sky dish, the picture quality is way better, but no bbc HD anymore they have gone dvb-s2 now. I get 2 channels from each card on the same multiplex, but they are normally all in use recording or streaming to the laptops etc.

Don't know your choice of graphics card but make sure it has a large heat sink and maybe put a fan near it.

You don't list any remote control, you can use the one that comes with the nova-t but you will spend more time throwing it at the box cos it's too slow and mis-reads, very frustrating.
Choose a Microsoft one, the important part is the IR receiver, must be good for for MCE. There usb and have there own interrupt, so you don't have to wait for the TV card. 

I use DVDfab on windows to rip my dvd's to the Mythbox drives over the network and Audio CD extractor from ubuntu for the music cd's.  I've stuck with 10.04 myth .24 for now as it all works well, even through there are a few missing bit's.

Hope this helps

---

### Post by Alistair1234 on 2011-07-25
Thanks for your replies!

Regarding the temperature in the case, I was thinking of a similar set up to this: [http://hardforum.com/showpost.php?p=1037260825&postcount=564]("http://hardforum.com/showpost.php?p=1037260825&postcount=564") (without the enormous graphics card!) but will ditch the top and bottom case fans and have the other 3 case fans connected to the bundled fan controller. I would also flip the psu to draw air out of the case and over the tv tuner + graphics card. Would this keep the temp down? I might consider the define R3 case if not?

Will look again at a quiet/green hdd - thanks for pointing that out.

My main worry is compatibility with Ubuntu - I have read that it has some issues with Sandy Bridge cpu's, but is this just confined to the graphics processing element and therefore not relevant for me as I will have discrete graphics?

I really don't want to buy myself into a corner that some relatively simple tweaks can't get me out of!

And finally!

Would the Zalman ZM400-ST PSU be suitable? More/less power needed considering potential future upgrades?

---

### Post by AlecJ on 2011-07-25
The case photo you show is a tower, not for under the telly. But it looks like it should be cool enough, time will tell. My motherboard has 4 PCI slots for the TV cards so it fills the case well.

I only use AMD 64 chips, never been a problem using 64bit Mythbuntu.

As for the power supply, my Mythbox is always on and I normally get 18 -24 months from a power supply or the fan, once it's becomes too noisy I have to swap it out. Last one popped the RCD on the ring main and produced a puff of smoke. I always have a spare one, this time it's a Storm ice from ebay about £30.
heres another good one ebay item 130390692981

---

### Post by itlarson on 2011-07-26
Strange that your PSU's keep burning out, I've used the same Corsair PSU (~450w) for almost four years.  If it's just the fan, that can always be replaced separately.  My system uses a custom built case with two 120mmx800rpm intake fans with the PSU  and one 92mm fan as exhaust fans.  The 92mm is throttled to about 1000rpm to keep it quiet and the PSU fan is a very slow  turning 120mm.   I use the AMD 4850e (45w max) with a small heat-pipe cooler.  There is no separate CPU fan, as the 92mm draws air directly off the heat-pipe.  The CPU runs in the mid to high forties celsius, the GPU in the high fifties, and the drives in the high thirties.  Under load temps increase no more than 10c.  I an using Mythbuntu 10.04 64 bit with Mythtv 23.1.

---

### Post by AlecJ on 2011-07-27
> **itlarson said:**
> Strange that your PSU's keep burning out, I've used the same Corsair PSU (~450w) for almost four years.  If it's just the fan, that can always be replaced separately.  My system uses a custom built case with two 120mmx800rpm intake fans with the PSU  and one 92mm fan as exhaust fans.  The 92mm is throttled to about 1000rpm to keep it quiet and the PSU fan is a very slow  turning 120mm.   I use the AMD 4850e (45w max) with a small heat-pipe cooler.  There is no separate CPU fan, as the 92mm draws air directly off the heat-pipe.  The CPU runs in the mid to high forties celsius, the GPU in the high fifties, and the drives in the high thirties.  Under load temps increase no more than 10c.  I an using Mythbuntu 10.04 64 bit with Mythtv 23.1.

Well with 4 drives (5 with the DVD) 4 Sat cards powering 4 LNB's, plus I forget to vacuum the dust out often enough. I guess I'm not very kind to them really.
The one that popped the RCD was a expensive one, into 3 figures.
I'm not impressed by brand names any more, I just get the cheapest now they seem to last just as long. As long as the case is full of holes and there is a large fan that turns slowly so as it's quiet.
I spent a lot of time finding rubber mounted fans for the case and cpu and they work well. I gave up on the water cooled systems the glycol damaged my laminate flooring when it leaks and they always leak after a while, shame it was very quiet.

---

