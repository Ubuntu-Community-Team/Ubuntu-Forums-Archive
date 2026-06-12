---
title: "Looking for PCI digital sound card"
date: 2009-12-03
forum: Multimedia Software
---

### Post by sailor420 on 2009-12-03
Hi all,

Apologies if someone has covered this before, but my cursory search didn't turn it up.

I'm looking to drop a digital audio card into an older desktop running Ubuntu 9.4 so that I can get surround sound out to my receiver. Unfortunately, the machine is older and only has PCI (not PCIe) slots, so this restricts things a bit

Is there any concensus card (or at the least chip that I should be looking for) that seems to work out of the box in Ubuntu? I know that digital audio is not always the easiest thing to get working in Linux, so I'd like to minimize the headaches if possible.

Thanks!

---

### Post by markbuntu on 2009-12-04
I have a SIIG Soundwave 7.1 PCI card which uses a c-media chipset and have had zero problems with it using Hardy and Intrepid and Jaunty and Karmic. It has digital in and out and 7,1 surround and it is cheap but good quality sound. If you are not looking for an audiophile or professional card this would probably be a good choice. Diamond also makes inexpensive PCI cards with the same chipset and those also work OOB.

When you install a new sound card be sure to reinstall ALSA so it can be automagically detected properly and the correct driver loaded. This will avoid any problems.

You could also probably use a soundblaster audigy card but some people have reported problems getting them working initially.

---

### Post by sailor420 on 2009-12-04
Mark,

Thanks for the reply. That looks exactly like what I'm looking for. Definitely don't need anything audiophile quality, as it will be used mostly to play DVDs and such.

Thanks again!

---

### Post by Maheriano on 2009-12-04
Check out the [Chaintech AV710]("http://www.newegg.com/product/product.aspx?item=N82E16829120103") that I'm using. It gets nothing but crazy good reviews on every site it's posted on because of its onboard Envy24 chipset. The unfortunate part is I tried to set it up in Ubuntu 8.1 and found out there weren't any drivers to actually use the digital SPDIF output for it but haven't tried it with Ubuntu since then.

---

