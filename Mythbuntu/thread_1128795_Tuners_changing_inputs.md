---
title: "Tuners changing inputs"
date: 2009-04-18
forum: Mythbuntu
---

### Post by dotnick on 2009-04-18
It's almost funny.... the more advanced Ubuntu gets, the more things screw up.  I never had any problems with my tuner cards changing from /dev/video0 to /dev/video1 and vice versa until I upgraded to Intrepid.  I wouldn't have upgraded if my Gyration remote were better supported in 64 bit on Hardy.... oh well </vent>

I've found information on setting up udev rules for the analog sides of the pcHDtv5500 and Hauppage 1600 cards, which are working perfectly now.  But, ah, it's not over.  I'm using the digital portion of my Hauppage card for over the air, (analog is for cable), but my Hauppage card seems to change inputs as well.  In mythtv-setup, the two options are 0 and 1, and depending on the mood of ubuntu for that boot, it's anybody's guess where it's going to land.  Roulette anyone?

Is there any way whatsoever to control this?  It's not given the device name like the analog side is, so I didn't think another udev rule would do the trick, but maybe i'm missing something?

I can't be the only one with this problem, but I sure haven't found anything else for the digital.

please advise,
dotnick

---

### Post by ian dobson on 2009-04-18
Hi,

A udev rule should solve the problem. Have a look here [http://ubuntuforums.org/showthread.php?t=1070912&highlight=udev](http://ubuntuforums.org/showthread.php?t=1070912&highlight=udev) to see how to put together a udev rule.

Regards
Ian Dobson

---

### Post by dotnick on 2009-04-18
The way I understand the problem is that the new udev rules create a symlink to /dev/<videoX> on boot based on the rule provided.  So the new symlink /dev/mynewsymlink could point to either /dev/video0 or /dev/video1, which is fine for the analog portions of the cards.  But I still don't see how this is going to help the digital side.

The setup doesn't allow me to point it to a symlink, but rather the 1st card or the 2nd card.  And I'm assuming that the 0 and 1 have something to do with the /dev/video0 and /dev/video1 names.  So if card X was /dev/video1 before, and the system reboots and it is now /dev/video0, the mythtv-setup for the DVB card is not dynamic in that it will not change from being the 2nd card to the 1st, ie. card 1 to card 0, thus because of the card types V4L vs MPEG the card will not function without going back into mythtv-setup.

I'm not claiming to know too much about this, but this seems to be my experience so far.  And it never happened in 8.04.  

I've tried the other option in the modprobe.conf as well, but it doesn't seem to do anything for me as far as telling the kernel which video card should be assigned which /dev/videoX link.

---

### Post by utar on 2009-04-18
You can usually set the device number via an option in /etc/modprobe.d/options.  For example in my file I have the line:

options dvb_usb_dw2102 adapter_nr=5

Which forces my USB sat box to dvb adapter number 5, leaving adapter 0 free for my TV card.  Without this both cards kept swapping in a similar way to what is happening to you.

You can use the modinfo command along with the module name your cards are using to find if they have a similar option to mine.


Utar

---

### Post by dotnick on 2009-04-18
Ahh.... thank you.  I read that this method only seems to work on V4L devices, but fortunately the pcHDtv5500 is a V4L device.

so I added the line

options cx88-dvb adapter_nr=5

to /etc/modprobe.d/options

and when I rebooted, the pcHDtv5500 was sent to device 5 and the Hauppage card was on 0.

---

### Post by blackest_knight on 2009-04-20
I went through this a couple of years ago , I'm going through it again today. I have forgotten the details but I seem to remember I set a udev rule which said something like this pci card slot wants to be assigned to this device and this other card in this other pci card slot wants assigning as another device. 

It should get them right each time unless your in the habit of pulling your cards between boots. 

or did i actually i think i might have tried another tactic of blacklisting the driver for one card and then enabling it in modules later Essentially just forcing the system to always deal with the other card first. 

It may have been a third way using an alias I seem to remember setting it up so dev/car was one card( it had a security camera watching my car) dev/mercury which was a mercury tv card and in this way it didnt matter which dev device it was since I referred to them by individual names.

---

