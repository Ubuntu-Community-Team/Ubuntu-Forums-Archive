---
title: "USB TV Cards ..."
date: 2010-01-29
forum: Multimedia Software
---

### Post by badger_fruit on 2010-01-29
Hi guys
I have Windows XP running Media Portal but it's pretty dire in comparison to Myth TV.
Anyway, I want to migrate the two USB tuners I have on Windows XP to Mythbuntu.

The cards are 1 x Freecom DVB-T (Art number 25451-Rev3) and 1 x Compro Videomate U80. I tried "plug and play" (well, plug in, reboot) but I can't find them under /dev/video or in the "select a card" screens in Myth Backend setup.

Does anyone have experience with either card and if so, please can they help me to get them working for Mythbubtu 9.04 / Myth TV 2.2.

Many thanks and all the best
Badger

---

### Post by sports.car.guy on 2010-01-29
> **badger_fruit said:**
> Hi guys
I have Windows XP running Media Portal but it's pretty dire in comparison to Myth TV.
Anyway, I want to migrate the two USB tuners I have on Windows XP to Mythbuntu.

The cards are 1 x Freecom DVB-T (Art number 25451-Rev3) and 1 x Compro Videomate U80. I tried "plug and play" (well, plug in, reboot) but I can't find them under /dev/video or in the "select a card" screens in Myth Backend setup.

Does anyone have experience with either card and if so, please can they help me to get them working for Mythbubtu 9.04 / Myth TV 2.2.

Many thanks and all the best
Badger


In order to get them up and running you need to know if they are supported first. Before coming out here have you googled to see if there is support for your two DVB cards with Linux? Are they supported?

---

### Post by badger_fruit on 2010-01-29
> **sports.car.guy said:**
> In order to get them up and running you need to know if they are supported first. Before coming out here have you googled to see if there is support for your two DVB cards with Linux? Are they supported?

Well a google search for both cards, suffixed with "ubuntu" seemed to return a fair few results, I understand that the Freecom one is supported by the 2.6 kernel with "updated firmware" from previous experience trying to get it to work under OpenSuse quite some time ago (although I gave up trying after so long).

The Compro one is new to me and there's no mention of linux in the manual or on their website - but it's rare that linux is mentioned even if the particular hardware works, you have to find out for yourself.

I'll plug them in again later and lsusb them; then I'll just google it.

---

### Post by steefjeqv on 2010-01-30
Hi,

If you're using DVB (or ATSC) you might want to try the PPA of the VDR team :

[https://launchpad.net/~the-vdr-team/+archive/vdr-ubuntu-karmic]("https://launchpad.net/~the-vdr-team/+archive/vdr-ubuntu-karmic")

Or their Ubuntu based distribution :

[http://www.yavdr.org/]("http://www.yavdr.org/")

Greetings,
Steven

---

### Post by sports.car.guy on 2010-01-30
> **badger_fruit said:**
> Well a google search for both cards, suffixed with "ubuntu" seemed to return a fair few results, I understand that the Freecom one is supported by the 2.6 kernel with "updated firmware" from previous experience trying to get it to work under OpenSuse quite some time ago (although I gave up trying after so long).

The Compro one is new to me and there's no mention of linux in the manual or on their website - but it's rare that linux is mentioned even if the particular hardware works, you have to find out for yourself.

I'll plug them in again later and lsusb them; then I'll just google it.


One place to check for support is the wiki at linuxtv.org. It is part of v4l project.

---

### Post by prju68 on 2010-01-30
Sorry to grab this thread, but as I am trying do the same thing perhaps this might help.

If i do a lsusb the device is listed with the ID 185b:0150.

Over at linux TV[ http://linuxtv.org/wiki/index.php/Rtl2831_devices]("http://linuxtv.org/wiki/index.php/Rtl2831_devices") this is listed as being supported.

So I downloaded the source, compiled and installed. 

This generates a lot of drivers in the directory:

/lib/modules/2.6.31-17-generic/kernel/drivers/media/video

but none of these look like they have anything to do with the U80 video mate card... 

I'm guessing therefore that something has to be done to the source to generate a specific driver for the U80.  I dont know how to do that or how Linux knows at boot time to assign which driver to which item of hardware.

If I run at HWINFO and  it says the driver is "usb" which I guess is some generic driver for anything USB when the driver cannot be found.

Any suggestions as to where to look next would be great.

Thanks
Peter

---

