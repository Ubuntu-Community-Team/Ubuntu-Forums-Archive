---
title: "Cannot mount/connect with Mp3player"
date: 2008-09-16
forum: Multimedia Software
---

### Post by Klot on 2008-09-16
Hi people,
first of all, I just switched from XP to Ubuntu and I have pretty much no idea what I am doing so I might need a tutorial right from the beginning. 
When I plugin my new,cheap Coby 4Gb flash mp3player, all I get is this:
niko@niko-desktop:~$ lsusb
Bus 008 Device 006: ID 10d6:2300 Actions Semiconductor Co., Ltd 

when I type sudo fdisk -l, I only see my Linux drives but nothing else. Nothing is mounted in the filesystem either, and I cant access anything with Rhythmbox which probably just makes sense since nothing is showing up in the fdisk list.

Where to start?

thanks
Nick

---

### Post by Klot on 2008-09-21
well, no one has an idea yet. Maybe this will help. After typing sudo tail -f /var/log/messages and then connect the player I only get the following message:

Sep 21 20:26:18 niko-desktop kernel: [29889.502461] usb 5-5: new high speed USB device using ehci_hcd and address 3
Sep 21 20:26:18 niko-desktop kernel: [29889.639343] usb 5-5: configuration #1 chosen from 1 choice

Thats it, nothing else. What is missing?

thanks

---

### Post by ametalguitarist on 2009-06-15
In Jaunty with a coby 512mb /radio-mp3 player I had a little success opening nautilus as root and finding the folder with the music in it and swapping for the folders I wanted to hear.  Everything changed fine on the player except that the display had Chinese characters but the folder browsing inside the player had english.  I wasn't able to reproduce those results so I'm not sure how long I'll be stuck with these songs on the player.  After installing the mtp libraries It's recognized in Rhythmbox but no other action can be taken and in the file browser it's labeled ALi Corp.audio player but cannot be mounted except as root, and that only once so far.  I wish I would have copied the device files while I was in there.  When I get it to do it again I'll post it.

---

### Post by ametalguitarist on 2009-06-15
retracted

---

### Post by carl99fan on 2009-08-10
On the Colby go to:

"There is one configuration setting necessary for the player to happily talk to Ubuntu 8.04 Linux over USB:
Setup -> System -> USB Mode -> MSC

"

Plug it in.... your good.

---

### Post by Tom.Molyn on 2009-11-06
Hello i have a Coby MP815-8G Media Player and i am having similar issues connecting it to Ubuntu

after a few seconds of being connected the player switches between the **main menu** and **USB Connected** states

this is the log i get using
_sudo tail -f /var/log/messages_
[[IMG]http://img509.imageshack.us/img509/6281/cobyerror.th.png[/IMG]]("http://img509.imageshack.us/img509/6281/cobyerror.png")
This is the **Error** i get after i **_Safely remove the drive_**
[[IMG]http://img32.imageshack.us/img32/2153/cobyerrorremoving.th.png[/IMG]]("http://img32.imageshack.us/img32/2153/cobyerrorremoving.png")
This is the **_Properties_** of the Coby/RockChip USBDISK
[[IMG]http://img509.imageshack.us/img509/9416/cobyerrordetails.th.png[/IMG]]("http://img509.imageshack.us/img509/9416/cobyerrordetails.png")

The Coby Documentation says supported operating systems are Windows and Mac. i attempted to use wine with no success.
the Coby was bought on Nov 4, 2009

---

