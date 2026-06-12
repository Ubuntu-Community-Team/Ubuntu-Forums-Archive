---
title: "PCI Capture cards based on Phillips SAA7130 chipset?"
date: 2008-10-15
forum: Mythbuntu
---

### Post by Dragnovich on 2008-10-15
Hello I just found the mythbuntu proyect and have some questions.

First than all, Im in mexico so is not very easy to get specific cards and models as in the USA, tha you can shop virtually in hundreds of e-shops.

Here we are restricted to the importers, and what do they import (I cant find a dealer that ships the products to mexico too), so browsing all options I have here, I found that they dont sell none of the models that you have tested, how ever they sell many TV Capture cards based in the "Phillips PCI Capture (SAA7130)" chipset.

So is this chipset supported by the mythbuntu ??

Thanks!

---

### Post by ian dobson on 2008-10-15
Hi,

Have a look here [http://www.linuxtv.org](http://www.linuxtv.org)

Regards
Ian Dobson

---

### Post by jobinau on 2009-02-18
Quick answer to your question:
Yes! SAA7130 is supported, but it uses the SAA7134 driver. 
infact Philips SAA7130 is a scale down version of SAA7134 for which linux driver is available.
i mean, you need to load the saa7134 module like:

modeprobe saa7134 

I am already using a SAA7130 based tuner for viewing TV.
here i documented how you can do that.
[http://jobinau.googlepages.com/saa7130basedtvtunercardunderlinux](http://jobinau.googlepages.com/saa7130basedtvtunercardunderlinux)

---

### Post by klc5555 on 2009-02-18
> **jobinau said:**
> Quick answer to your question:
Yes! SAA7130 is supported, but it uses the SAA7134 driver. 
infact Philips SAA7130 is a scale down version of SAA7134 for which linux driver is available.
i mean, you need to load the saa7134 module like:

modeprobe saa7134 

I am already using a SAA7130 based tuner for viewing TV.
here i documented how you can do that.
[http://jobinau.googlepages.com/saa7130basedtvtunercardunderlinux](http://jobinau.googlepages.com/saa7130basedtvtunercardunderlinux)


You will likely need to download and install the nxt2004 firmware for one of these cards, and you'll also likely need to specify the card and tuner parameters as modprobe options, since most of these cards are so cheaply produced that modprobe has trouble identifying one from another. Once they are configured, however, they work great.

The mythtv howto for the Avermedia A180 tells how to get the firmware for these cards. 

[http://www.mythtv.org/wiki/AVerTV_HD_A180](http://www.mythtv.org/wiki/AVerTV_HD_A180) 

The list of cards is most easily found on the Gentoo wiki:

[http://en.gentoo-wiki.com/wiki/Saa7134](http://en.gentoo-wiki.com/wiki/Saa7134)

The list of tuners is found here: 

[http://www.gentoo-wiki.info/SAA7134#tuner](http://www.gentoo-wiki.info/SAA7134#tuner)

So that, for example,to load my AverMedia A180 properly via modprobe, the command was;

modprobe saa7134 card=75 tuner=68

And finally, though this doesn't usually affect Ubuntu, it's hardly documented anywhere: if your I2c support is compiled straight into the kernel, the nxt-2004 firmware absolutely, positively will not load. I2c support must be done as a module. 

Like I said, not usually a problem with Ubuntu, unless you've done some peculiar kernel compiling. But in some distros it will stop you dead with one of these cards until you figure it out.

Cheers! :)

---

