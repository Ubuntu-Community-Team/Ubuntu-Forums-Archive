---
title: "TV Tuner Card?"
date: 2006-03-21
forum: Multimedia &amp; Video
---

### Post by Kurt` on 2006-03-21
Hi,

I recently took a look at the HCL for Ubuntu (at least I hope this is the official one):
[http://www.tldp.org/HOWTO/Hardware-HOWTO/other.html#AEN16431](http://www.tldp.org/HOWTO/Hardware-HOWTO/other.html#AEN16431)

I've decided to buy a TV Tuner card, as I want to record TV shows that I can't watch (due to schedule conflicts). However, I want it to work perfectly in linux! :)

I took a look at some major sites (CompUSA, Best Buy, etc.), and none of their product descriptions mention what chipset/driver the tuners use. How am I supposed to determine if a card will easily work with Ubuntu or not?

I hope to learn a bit more about how video works with linux, and I think this is a good excuse to force myself to learn it. :D

---

### Post by Stormbringer on 2006-03-22
For normal TV tuner cards take a look here:
[http://linux.bytesex.org/v4l2/](http://linux.bytesex.org/v4l2/)

For a TV tuner card featuring an MPEG-2 encoder or DVB capabilities, take a look here:
[http://ivtvdriver.org/index.php/Main_Page](http://ivtvdriver.org/index.php/Main_Page)

On both sites you will find a list of supported devices / chipsets.

Cheers,
Storm.

---

### Post by RoboJ1M on 2006-04-04
And here
[http://www.linuxtv.org/wiki/index.php/Main_Page]("http://www.linuxtv.org/wiki/index.php/Main_Page")

I can confirm that the TwinHan Ter VP-3021 (PCI, one RF in, nothing else, DVB-T tuner, VERY CHEAP) works. But you need to add dst and dvb_bt8xx to your /etc/modules file.

J1M.

---

