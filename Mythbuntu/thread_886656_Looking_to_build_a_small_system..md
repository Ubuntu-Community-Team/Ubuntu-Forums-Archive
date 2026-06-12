---
title: "Looking to build a small system."
date: 2008-08-11
forum: Mythbuntu
---

### Post by dabone on 2008-08-11
I'm looking at a mini-itx as a base for a mythbuntu system.
Probally going to use the new intel dg45fc board and then go external usb tuners.

I'm in the USA and would like to know if 2 usb tuners are supported / advisable for both analog cable and qam tuning?

It there enough bandwidth over usb 2.0 connects for dual tuning?
I'm trying to keep the tuners out of the box because of thermal concerns.

Windows MCE compatibility would also be a plus. (I'm a system builder and would like to be able to sell this box with a MS and Linux option)


Thanks.

Later,
dabone

---

### Post by bmwman on 2008-08-11
I just ordered my new box. Here is what I got:

Qty.	
1 Intel Core 2 Duo E8400 Wolfdale 3.0GHz LGA 775 65W Dual-Core Processor Model BX80570E840	$169.99

1:Patriot Extreme Performance 2GB (2 x 1GB) 240-Pin DDR2 SDRAM DDR2 800 (PC2 6400) Dual Channel Kit Desktop Memory Model PDC22G6400LLK 	$51.99

1 hec Black 0.7mm Thickness SECC Steel 7KJ9 Micro ATX Media Center / HTPC Case $69.99

1 GIGABYTE GA-EG43M-S2H LGA 775 Intel G43 HDMI Micro ATX Intel Motherboard $104.99
Grand Total:	$396.96

I also have the HDHomeRun dual HD tuner, ethernet attached. If you want you can go with the G45 Mobo but I thought G43 should be enough for me personally.

---

### Post by newlinux on 2008-08-11
[http://www.linuxtv.org/wiki/index.php/ATSC_USB_Devices](http://www.linuxtv.org/wiki/index.php/ATSC_USB_Devices)

---

### Post by dabone on 2008-08-11
BMW man, how are you going to get Non HD channels?

And newlinux, my question isn't just what tuners are compatible, but if anyone here has tried 2 external usb tuners at the same time, and if so did the usb bus get overloaded?

Is anyone here using a external usb stick that does qam and ntsc tuning?


Thanks,
Later,
dabone

---

### Post by newlinux on 2008-08-11
> **dabone said:**
> BMW man, how are you going to get Non HD channels?

And newlinux, my question isn't just what tuners are compatible, but if anyone here has tried 2 external usb tuners at the same time, and if so did the usb bus get overloaded?

Is anyone here using a external usb stick that does qam and ntsc tuning?


Thanks,
Later,
dabone

The hdhomerun can tune non HD channels, just not analog channels (not all digital channels are HD). So bmwman can't tune analog channels with that setup

Can't speak from experience, but there *should* be enough bandwidth for HDTV streams at once on a USB 2.0. HDTV mpeg-2 streams should rarely go more than ~20-25Mbps. I know you are looking for real world experience so I hope someone responds. I'd be interested to know as well.

---

### Post by McLogic on 2008-08-25
When you buy an ITX or mITX system, you spend more and get less (usually). By the time you have a 3.5 hard drive, 5.25" Optical, power supply, and a couple of fans, the board size is not that important.

I would suggest getting a **Micro-ATX** system, as you will spend less and get more. You will also have more choices. 

If you have a part fail, you will want one same-day. If you have an odd power supply, board, ect., you are less likely to be able to get a replacement quickly and/or locally. 

Also, think about if you are going to do anything else with your computer. Having 4 expansion slots can be handy. 
[LIST]
[*]Want a TV tuner card (or two)? 
[*]Want a hardware RAID card? 
[*]Want a second gigabit NIC?
[/LIST]

No to all?

Want to replace your board, case, power supply, etc. if you change your mind?

Take a look at the small mATX cases at the big online retailers. You will have lots of small options.

---

### Post by bmwman on 2008-08-25
> **dabone said:**
> BMW man, how are you going to get Non HD channels?

And newlinux, my question isn't just what tuners are compatible, but if anyone here has tried 2 external usb tuners at the same time, and if so did the usb bus get overloaded?

Is anyone here using a external usb stick that does qam and ntsc tuning?


Thanks,
Later,
dabone

The HDhomerun dual tuner can watch/record HD and regular channels. Also built in Mpeg2 encoder. I'm pretty happy with mine even though i'm using 50% of it's options.

---

### Post by notanatheist on 2008-09-06
Finding a suitable HTPC case is certainly tricky if you're trying to take advantage of size. [Antec Micro Fusion 350]("http://www.antec.com/us/productDetails.php?ProdID=15737#") looks to be a great fit with room for a full 5.25 optical. Low profile slots limit expansion but I'd recommend the Hauppauge HVR-1250 for a PCIe 1x low profile HDTV tuner. You can reduce your clutter that way. And hold out for 8.10 or download the latest alpha/beta if you pick up the DG45FC anytime soon.

I was originally going to use an AOpen S150 case but the power supply won't fit in with the stock low profile Intel cooler. Intel has a validated case list if you look at the specs for the board. Of course not every case option is on there but it is a starting point.

---

