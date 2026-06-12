---
title: "can I transfer video from camcorder to ubuntu via s-video?"
date: 2009-11-12
forum: Multimedia Software
---

### Post by kitty500cat on 2009-11-12
I have a Panasonic PV-GS120 MiniDV camcorder. I don't have a firewire port on my laptop so I can't transfer video that way. can I use the s-video port to transfer video from my camcorder to Ubuntu? I think my graphics card is an Intel GMA950, if that makes any difference. thanks. Jeremy

---

### Post by amoeba801 on 2009-11-13
As far as I'm aware, the Intel GMA950 is graphics out to you monitor only, no analogue video in. Check your computer documentation to see whether you have S-Video input.

If not, you'll need a new card that supports Analogue Video input; most TV Tuner cards do. If you don't have room for a card or, as I see in your case you have a laptop , you'll have to find a USB device that has analogue input - my guess is that these will be harder to find.

A very quick search on the web brought up this [product]("http://usbgear.com/computer_cable_details.cfm?sku=CTX-002&cats=125&catid=614,125").  Be warned though, you may have trouble finding a linux driver for it, depending on the chip inside. If it is something like the SAA7134, it is well supported.

The last problem is finding a capture method, most video editing software does not support analog input. I use a command line script using mencoder to grab my video.

You might decide from the above discussion to save yourself some hassle by buying a buying a PCMCIA Firewire adapter such as  [this]("http://www.topbuy.com.au/tbcart/pc/Sunix-IEEE-1394A-PCMCIA-Card-3-Port-p4612.htm") (note: this is an Australian site) - again make sure that there is a Linux driver for it.

---

### Post by amoeba801 on 2009-11-13
(dupe post, can't see how to delete, sorry)

---

### Post by kitty500cat on 2009-11-13
Thanks. I know I have an S-video in on my computer. I just didn't know what software to use. I'll check out mencoder. Thanks.

---

