---
title: "DVB-S2 help deciding on card"
date: 2011-03-28
forum: Mythbuntu
---

### Post by roundhay on 2011-03-28
I an looking to add a DVB-S2 dual tuner PCIe card to my myth box. I've a whole searching various forums have found a number of cards but there doesn't seem to be a consensus on which one if the best.

Based on price the one that is appealing is the TeVii S480

[http://www.dvbshop.net/product_info.php/info/p2352_TeVii-S480-Dual-DVB-S2-HDTV-PCIe-Diseqc-1-2-2-0-Low-profile.html]("http://www.dvbshop.net/product_info.php/info/p2352_TeVii-S480-Dual-DVB-S2-HDTV-PCIe-Diseqc-1-2-2-0-Low-profile.html")

But I have also found the following cards:

Digital Devices Cine S2
[http://www.dvbshop.net/product_info.php/info/p2332_Digital-Devices-Cine-S2---Duale-DVB-S2-HDTV--Rev--V5-5-.html]("http://www.dvbshop.net/product_info.php/info/p2332_Digital-Devices-Cine-S2---Duale-DVB-S2-HDTV--Rev--V5-5-.html")

Mystique SaTiX-S2 V2 CI Dual
[http://www.dvbshop.net/product_info.php/info/p2318_Mystique-SaTiX-S2-V2-CI-Dual--2xDVB-S2-CI-HDTV-MPEG4-H-264.html]("http://www.dvbshop.net/product_info.php/info/p2318_Mystique-SaTiX-S2-V2-CI-Dual--2xDVB-S2-CI-HDTV-MPEG4-H-264.html")

TBS 6981 PCI-E DVB-S2 Dual Tuner TV card
[http://www.tbsdtv.com/english/product/6981.html]("http://www.tbsdtv.com/english/product/6981.html")

I would be interested to hear if any of you have successfully used any of these cards in a myth set up.

---

### Post by winewood on 2011-03-28
Does it need to be a card?
I have a happauge 2250, but purchased a HDHomerun dual that is effortless.
If I had to do it over, I would have purchsed 2 of these to give me 4 tuners.
[HDHomerun]("http://www.cyberestore.com/hdhomerun-networked-hdtv-digital-dual-tv-tuner-refurbished.html")

Mythtv has all the software pre-installed and you simple go into the Tuner section and select add card.  It finds it automatically, and your good to go.

Boxes run out of room quickly, and I have found drivers that may or may not be supported may add to the frustration.

---

### Post by roundhay on 2011-03-29
Thanks for replying but I'm looking for a DVB-S2 card to pick up satellite broadcasts in the UK, Freesat. The HDHomerun lloks like a DVB-T / DVB-C tuner.

---

### Post by bance on 2011-03-29
maybe check the [mythtv wiki]("http://www.mythtv.org/wiki/Digital_Tuner_Cards") or [v4l]("http://linuxtv.org/wiki/index.php/DVB-S2_Devices") to see which cards are supported

---

### Post by Pantera116 on 2011-03-30
I am in the uk and got a tbs 6981 about 6 weeks ago.

It is not yet natively supported by v4l but there are linux drivers on the cd supplied with the card that will get it working. You basically follow the readme to compile the driver into your kernel.

Once working i got over 500 channels as you are not only picking up fressat but a lot of sky free to air stuff also.

I have reduced the channel count down to those that have over the air epg data. Please note that the channel numbers are all over the place. This is something i am planning to sort out at some point.

Of most interest to me was the bbc and itv hd channels. The 6 nations rugby, the f1 and the hd football has all looked really nice.

I have not used the supplied remote as i have sony ps 3 bluray remotes (bluetooth connected) set up already.

Only negative comment is the need to reinstall the drivers if you update the kernel.

---

