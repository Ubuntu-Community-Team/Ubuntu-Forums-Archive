---
title: "TV tuner card help please"
date: 2009-08-30
forum: Multimedia Software
---

### Post by pointyblue on 2009-08-30
Hi,

I'm trying to fix my parent's pc. It ran xp but installing sp3 caused bsod - and generally xp sucks compared to Ubuntu.

So I installed U9.04 and the machine runs better than ever except for one major thing: The TV tuner card isn't recognized which makes the damn thing unusable to them, sigh. (Tried it with Mythtv.)

The brand of the card is Elements and it's called Xpert TV7131.

Do any of you guys know how to make this card work? I'd hate to remove U9.04 and reinstall xp with security updates disabled...

---

### Post by Mrazek on 2009-08-30
Hi Pointyblue,

some common things: for first have a look to your TV card, to main chips and their types (for example many of analog cards use BT878 chip). Then try to google for bttv settings and try to change values in its configuration accordingly to chips on your card.

HTH...

---

### Post by Jose Catre-Vandis on 2009-08-30
Can you run "lspci -v" and "dmesg" and report back outputs that pertain to this card?

From your description it looks like it could be a Philips based product using SAA7131 tuner tda8275 or similar, in which case the drivers should be in the kernel.

Is it analog or dvb or hybrid? What programs other than mythtv (a bit over the top) have you tried to get it running with? Have you scanned for channels?

---

### Post by cascade9 on 2009-08-30
> **pointyblue said:**
> Hi,

I'm trying to fix my parent's pc. It ran xp but installing sp3 caused bsod - and generally xp sucks compared to Ubuntu.

So I installed U9.04 and the machine runs better than ever except for one major thing: The TV tuner card isn't recognized which makes the damn thing unusable to them, sigh. (Tried it with Mythtv.)

The brand of the card is Elements and it's called Xpert TV7131.

Do any of you guys know how to make this card work? I'd hate to remove U9.04 and reinstall xp with security updates disabled...

The Xpert TV7131 = Phillips SAA 713x. There is linux drivers for the SAA 713x, but they make not work with all versions of the card-

> You still need to configure I2C support in the kernel as for BT8x8 above, as well as making a module for saa7134 ("Device Drivers -> Multimedia devices -> Video For Linux -> Philips SAA7134 support"). If you can "modprobe saa7134" then your kernel already has this module.  IN 2.6.16, extra sound support has been split off into additional modules, saa7134-alsa and (apparently) saa7134-oss.  You don't need these to just watch TV.  See the sound section below.[http://www.wlug.org.nz/TvTunerCards](http://www.wlug.org.nz/TvTunerCards)

This might be handy as well-

[http://en.gentoo-wiki.com/wiki/Saa7134](http://en.gentoo-wiki.com/wiki/Saa7134)

BTW- if you do have to reinstall windows, DO NOT run it without security updating disabled if your going to hook it up to the net. Please. These enough zombie boxxen out there already. Go to teh control panel, updates, and set them to manual. Then you will get a list of updates, so you can get the security ones but not get SP3 (which has worked fine on the all the winXP boxes I've used) or other evilness like WGA.

---

### Post by pointyblue on 2009-08-31
Thanks so much for helping out guys.

Unfortunately they suddenly needed the computer back in a hurry so I had to just do an xp-install for now. Damn-damn-damn.

As soon as I can I'll get back to this.

Thanks again!

---

