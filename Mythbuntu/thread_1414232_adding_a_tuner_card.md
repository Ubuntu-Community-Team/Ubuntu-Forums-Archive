---
title: "adding a tuner card"
date: 2010-02-23
forum: Mythbuntu
---

### Post by linuxhippy on 2010-02-23
I have been really impressed by mythbuntu 9.10 over the last month.  I only have 1 PCI slot available and I want to get another tuner pci card.  I already have a Pinnacle 800i and want to buy another.  BUT-I'm not sure my computer can do this for 2 reasons.

I just read on the mythtv site that a soundcard is needed for each grabber since I don't have integrated sound.  So it seems that my SoundBlaster Audigy pci soundcard cannot handle another tuner card.  Is that right?

Also, do I need to split my coaxial cable signal with a cable splitter so that each tuner card has a coaxial input line or will the computer do this?

---

### Post by klc5555 on 2010-02-23
> **linuxhippy said:**
> I have been really impressed by mythbuntu 9.10 over the last month.  I only have 1 PCI slot available and I want to get another tuner pci card.  I already have a Pinnacle 800i and want to buy another.  BUT-I'm not sure my computer can do this for 2 reasons.

I just read on the mythtv site that a soundcard is needed for each grabber since I don't have integrated sound.  So it seems that my SoundBlaster Audigy pci soundcard cannot handle another tuner card.  Is that right?

Also, do I need to split my coaxial cable signal with a cable splitter so that each tuner card has a coaxial input line or will the computer do this?

1) You supposedly only need multiple sound cards with tuner cards that use separate lines-in to the soundcard for muxing, like a bttv card would use. Otherwise no. Assuming you're referencing [http://www.mythtv.org/wiki/Sound_card](http://www.mythtv.org/wiki/Sound_card)

2) You'll need to put a splitter on the coax.

---

### Post by ian dobson on 2010-02-23
Hi,

Most modern tuner cards don't need a seperate sound card, even an old (2004) WinTV analog card I have in my junk box doesn't need a sound card.

Some tuner cards have 2 tuner "ports", an in and an out. If the worst comes to the worst just use a T piece if your signal is strong enough.

Regards
Ian Dobson

---

### Post by nickrout on 2010-02-23
> **linuxhippy said:**
> I have been really impressed by mythbuntu 9.10 over the last month.  I only have 1 PCI slot available and I want to get another tuner pci card.  I already have a Pinnacle 800i and want to buy another.  BUT-I'm not sure my computer can do this for 2 reasons.

I just read on the mythtv site that a soundcard is needed for each grabber since I don't have integrated sound.  So it seems that my SoundBlaster Audigy pci soundcard cannot handle another tuner card.  Is that right?

Also, do I need to split my coaxial cable signal with a cable splitter so that each tuner card has a coaxial input line or will the computer do this?

Funny thing, googling 'Pinnacle 800i' comes up with a page on the mythtv wiki as the second entry. It has the answers to your questions, in particular: 

> The audio stream from this card comes in on its own audio device. If your system is like most you only have one sound card, and its device is typically /dev/dsp or /dev/dsp0. If this is the case then the audio device for your PCTV card is probably /dev/dsp1.

In other words the analogue side has it's own audio device. For the digital side of course it is immaterial.

Yes you will need to split the signal unless the card has a loopback (and the picture here [http://www.pctvsystems.com/Products/ProductsNorthAmerica/HybridproductsUSA/PCTVHDCard/tabid/171/language/en-US/Default.aspx](http://www.pctvsystems.com/Products/ProductsNorthAmerica/HybridproductsUSA/PCTVHDCard/tabid/171/language/en-US/Default.aspx) doesn't show a loopback). Splitters are cheap, but get good quality!

---

### Post by 4dognight on 2010-02-23
Have you considered the HDhomerun? It has 2 tuners and is external, so you dont need any slots available.

---

### Post by linuxhippy on 2010-02-23
this has all been helpful-thanks!

---

