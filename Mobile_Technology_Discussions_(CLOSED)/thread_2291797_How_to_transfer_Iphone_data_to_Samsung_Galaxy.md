---
title: "How to transfer Iphone data to Samsung Galaxy"
date: 2015-08-22
forum: Mobile Technology Discussions (CLOSED)
---

### Post by satimis on 2015-08-22
Hi all,

Please advise the easy way to transform Iphone data to Android (Samsung Galaxy)

Iphone data - tel contact, music etc.
Iphone - S3
Android - Samsung Galaxy S6
Computer - Ubuntu 14.04 desktop

I have been googling a while and found many suggestions on Internet such as via computer, icloud, google account etc.?

Thanks

Regards
satimis

---

### Post by tgalati4 on 2015-08-23
If you have a gmail account, then contacts and phone numbers will just show up on the Samsung once you set up the gmail account credentials.  I don't have an iphone, but I imagine there must be a gmail app on the iphone that allows moving Mac Contracts into gmail Contacts.

For moving iTunes music to Google Play:  [http://www.tomsguide.com/faq/id-2327837/export-music-itunes-google-play.html](http://www.tomsguide.com/faq/id-2327837/export-music-itunes-google-play.html)

I have not done this (since I don't use iTunes) so I don't know how well it works.  Perhaps someone else has and can respond how well this procedure works.

Connecting a Samsung Galaxy S6 to Ubuntu might be problematic.  Older phones seem to either need rooting or you had to jump through hoops to get MTP to work.

Some hints:  [http://ubuntuforums.org/showthread.php?t=2260887&highlight=connect+Samsung+Galaxy+S6](http://ubuntuforums.org/showthread.php?t=2260887&highlight=connect+Samsung+Galaxy+S6)

I don't have an S6, yet, so I can't comment on easy it is to connect to 14.04.

---

### Post by jerrylamos on 2015-08-24
This might help on the Samsung side.

Samsung Galaxy S3 set up for Verizon but using Tracfone service.
Plugged it into my PC with the charging USB cord.
Ubuntu in this case is Wily Development level  
"Files" mounted it but showed blank.

From a Launchpad post:

sudo gedit /etc/usb_modeswitch.conf
DisableSwitching=1

reboot.  Files showed my camera pictures on the micro SD card.

Easy to copy the jpgs from the micro SD card onto the PC. I don't see why the reverse wouldn't work as well.

For other data, I assume I'd have to copy to the micro SD card then to the PC.

I don't have an iPhone so I don't know how to get the iPhone data onto the PC.

Do note there are apps like SHAREit in the Google Play Store to do WiFi transfers.

Where did I find the magic incantation to change DisableSwitching from 0 to 1?  (No clue what this is about)  Wonders of Google search:

[https://answers.launchpad.net/ubuntu/+source/util-linux/+question/172101](https://answers.launchpad.net/ubuntu/+source/util-linux/+question/172101) 

BTW tried plugging the Samsung into Windows XP where all my pictures are - Microsoft download a USB driver, took a while, crashed XP horribly and had to reboot and remove the busted USB driver.  Yes I've got some Win 10's (free) just to see what people are talking about, do most everything with Ubuntu. :D

---

