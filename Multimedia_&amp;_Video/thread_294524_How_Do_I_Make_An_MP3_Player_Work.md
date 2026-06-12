---
title: "How Do I Make An MP3 Player Work?"
date: 2006-11-06
forum: Multimedia &amp; Video
---

### Post by mpierce on 2006-11-06
I can't seem to get my Creative Zen Vision:M to play with Edgy.

I've installed gnomad2, libnjb5, libmtp2

Gnomad2 on start says: No Jukeboxes found on USB bus

Dmesg shows: 
[17188308.420000] usb 4-1: new full speed USB device using uhci_hcd and address 5
[17188308.584000] usb 4-1: configuration #1 chosen from 1 choice

lsusb shows: 
Bus 004 Device 005: ID 041e:413e Creative Technology, Ltd
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 003: ID 059f:0651 LaCie, Ltd
Bus 003 Device 002: ID 059f:0651 LaCie, Ltd
Bus 003 Device 001: ID 0000:0000
Bus 001 Device 005: ID 04a9:2213 Canon, Inc. LiDE 50/LiDE 35
Bus 001 Device 004: ID 413c:3010 Dell Computer Corp. Optical Wheel Mouse
Bus 001 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000

Konqueror launches and shows
camera://Creative Zen Vision@[usb:004,005]/
   Could not read file /.

The Creative Zen Vision:M is there as Bus 004 Device 005.

I cannot create a mount point as my computer is a Dell with Sata drive and I have:
   /dev/sda1 windows xp
   /dev/sda3 /
   /dev/sda4 /home
   /dev/sda5 vfat data
   /dev/sda6 swap
   /dev/scd0 cdrom

The LaCie drives listed under lsusb are removable hard drives and they work perfectly.

I shouldn't have to create a mount point as it should just work like the LaCie drives and my USB key

Any thoughts on how to get this mp3 player to work?

---

### Post by jadedjay on 2006-11-19
I would like to know also as I have been playing around with the usb settings  myself with no luck. 

I found the same results using the gnomad driver (which worked fine for my older Creative Zen players)

---

### Post by jadedjay on 2006-11-19
Maybe check this out. 

We apparantly need to add another library to make it work

[http://fsiu.uwc.ac.za/kinky/index.php?module=wiki&action=wikilink&pagename=CreativeVisionMonUbuntuDapper](http://fsiu.uwc.ac.za/kinky/index.php?module=wiki&action=wikilink&pagename=CreativeVisionMonUbuntuDapper)

I havent got the time to try it now.

---

