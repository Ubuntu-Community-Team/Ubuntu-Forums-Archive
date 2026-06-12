---
title: "Mythfrontend on usb flash stick?"
date: 2009-02-14
forum: Mythbuntu
---

### Post by jape42 on 2009-02-14
Hi All,

Has anyone come across instructions on how to install a mythbuntu frontend on a flash drive?  I've just done a regular install, and although this works, it results in a fair amount of "blockiness" when accessing the flash disk.  I've also seeing screen blanking (TV + HDMI) which I've attributed to the slow flash drive (until I prove otherwise).

I have 4G ram and ideally I'd like to boot from flash into a ramdisk, but also be able to modify the system significantly ( ie try out dev versions of the radeonhd driver, build mplayer from svn etc).

I tried these instructions:

[http://www.pendrivelinux.com/usb-xubuntu-810-install-via-the-usb-creator/#more-664](http://www.pendrivelinux.com/usb-xubuntu-810-install-via-the-usb-creator/#more-664)

Any they resulted in the liveCD on the USB drive, but after trying to configure the front end, it no longer booted.

Any pointers?

regards

jp

---

### Post by jayman8547 on 2009-02-15
I am booting to a 4gb SDHC card and everything is great. I just did a regular install to the flash card and I am able to run all the myth with all latest drivers and vdpau with no ill effects.  If you are gettting "blockiness" it sounds like it might be the speed of the card.

---

### Post by jape42 on 2009-02-15
> **jayman8547 said:**
> I am booting to a 4gb SDHC card and everything is great. I just did a regular install to the flash card and I am able to run all the myth with all latest drivers and vdpau with no ill effects.  If you are gettting "blockiness" it sounds like it might be the speed of the card.

Thanks for the data point.  You are using a USB adapter to the SDHC card?  What class is the SDHC card?  SDHC memory has gotten cheaper, so maybe this is something I can try.

Truthfully I haven't proved that the video (hdmi) flashing is due to the slowness of the usb stick, but it seems like the most likely cause.

jp

---

### Post by ian dobson on 2009-02-15
Hi,

I'm using a 8Gb x300 CF card in a CF -> SATA adapter and everythings working very well and quiet. I'm been running like this for about 6 months now and have not seen any problems with "flash ware out".

My recordings/tuners are in a different box well out of hearing:)

I'm also using the vdpau backport of MythTV 0.21 since about 6hours and am not seeing any problems.

Regards
Ian Dobson

---

### Post by jayman8547 on 2009-02-15
Sandisk Ultra II 15mb/s with supplied usb adapter.  Not sure of the class but 15mb/s is only a write speed of 100x so I guess that might eliminate the card speed being an issue.  I had an older A-data 4gb CF card with an IDE to CF adapter that worked with an ubuntu mini install.  I wanted to use it in my frontend but it won't boot after I load the OS on it.  Since I had an extra sdhc card laying around from the camcorder I grabbed it and installed mythbuntu desktop.  Going on about 4 months with no issues.....

On a side note about the flexibility of installing to flash memory, not only is it silent but it is quite flexible.  The only noise from my frontend is from the 2 120mm case fans and I can only hear that when there is no other noise in the room.  Also, yesterday I installed all the vdpau stuff on my laptop and I have to say I am quite impressed.  Since I have my main frontend loaded on a flash card and really stable I don't want to mess with it.  I am going to buy a couple more sdhc cards or usb sticks and just create base mythbuntu frontend filesystems on them that way I can play around with vdpau without messing with the stable version.

For the record my frontend is an ASUS M3N78-VM with audio and video over hdmi.  I haven't had any video issues that I can attribute to the OS on a flash card.

---

### Post by jape42 on 2009-02-15
> **jayman8547 said:**
> Sandisk Ultra II 15mb/s with supplied usb adapter.  Not sure of the class but 15mb/s is only a write speed of 100x so I guess that might eliminate the card speed being an issue.  

Is the the card you are using?:
[http://www.sandisk.com/Products/Item(2582)-SDSDRH-032G-A11-SanDisk_Ultra_II_SDHC_32GB_High_Performance_Card.aspx](http://www.sandisk.com/Products/Item(2582)-SDSDRH-032G-A11-SanDisk_Ultra_II_SDHC_32GB_High_Performance_Card.aspx)

If so, one of the reviews claims these cards have 15MB/S read and 9MB/S write.  I guess this would put this card into class 9 (as far as I can tell from wikipedia), which is quite a bit above what a cheap SDHC card would do (ie class 4 seems pretty common). 

The read speeds of this card are not totally dissimilar from my Kingston 4G DataTraveller usb stick:

root@vcr3:/home/jape# hdparm -tT /dev/sda
/dev/sda:
 Timing cached reads:   1510 MB in  2.00 seconds = 755.55 MB/sec
 Timing buffered disk reads:   50 MB in  3.10 seconds =  16.11 MB/sec

I too am hoping for a silent mythfrontend, but my fans are pretty loud right now.  I need to get things working properly first, before I tackle this.

I personally love the ease of backup.  Stick the usb stick into my desktop and 'cat /dev/sdd > backup.file' and I can safely experiment all I want.
 

regards,

jp

---

### Post by jayman8547 on 2009-02-15
This is the card
[http://www.newegg.com/Product/Product.aspx?Item=N82E16820171347](http://www.newegg.com/Product/Product.aspx?Item=N82E16820171347)

I guess it is a class 9.  Like I said in the previous post, I use these for for my camcorder and I needed something quick 4 months ago...

jayman8547@Tattooine:~$ sudo hdparm -tT /dev/sdb
/dev/sdb:
 Timing cached reads:   1886 MB in  2.00 seconds = 943.64 MB/sec
 Timing buffered disk reads:   42 MB in  3.02 seconds =  13.89 MB/sec

seems the speeds are similar to what you have.  Now you have me wondering if this is a flash card vs usb stick issue.  I know that each brand has their +'s and -'s (never ever ever buy transcend btw).  Maybe I should buy the exact same cards for my tests...

---

### Post by jape42 on 2009-02-16
Thanks for the info.  Since our devices are not that far off, maybe this is not the cause of my problems.  I did a quick write test and I'm getting 6-7 meg/sec, which I would think should be OK.

My desktop has almost identical hardware, so I guess I can try the same setup there and see if it is reproducible in a non flash based system.

regards

jp

---

