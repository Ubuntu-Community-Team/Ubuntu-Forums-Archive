---
title: "DMA issues"
date: 2006-06-06
forum: Multimedia &amp; Video
---

### Post by jmills on 2006-06-06
Upgraded to Dapper.

CD ROM skips.  Sounds for all the world like a DMA problem.

critical section of /etc/hdparm.conf reads:


#/dev/cdroms/cdrom0 {
#	dma = on		   
#	interrupt_unmask = on
#	io32_support = 0
#}

So, I assume DMA is on.  Anyone got any other bright ideas?

---

### Post by gerbman on 2006-06-06
[QUOTE=jmills]Upgraded to Dapper.

CD ROM skips.  Sounds for all the world like a DMA problem.

critical section of /etc/hdparm.conf reads:


#/dev/cdroms/cdrom0 {
#	dma = on		   
#	interrupt_unmask = on
#	io32_support = 0
#}

So, I assume DMA is on.  Anyone got any other bright ideas?[/QUOTE]Try uncommenting that section (removing the pound characters).

---

### Post by jmills on 2006-06-06
I see said the blind man, but he didn't really see at all.

Kind of bone-headed.  Ok, I uncommented it.  Still same problem.

Actually the entire /etc/hdparm.conf file has ONLY comment lines.

Is some other file configuring the CDROM?

Thanks for waking me up this morning.

J.

---

### Post by gerbman on 2006-06-06
Try [this]("https://wiki.ubuntu.com/DMA?highlight=%28dma%29") guide.

[QUOTE=jmills]Thanks for waking me up this morning[/QUOTE]Haha, I'm a man who enjoys his sleep, too :-D

---

### Post by jmills on 2006-06-06
Hmmmm.  

Virtually the entire /etc/hdparm.conf file was commented out.

I deleted it all, leaving only the last part of the Ubuntu wiki file.  Still, same problem.  Not sure about what's the bug.  

One thing I don't really get -being pretty new to Linux is how to identify the devices.  Click on the "computer" icon, and you can view the hard drives, and the CD ROMS and thumb drives, but they don't seem to have the Winblows "C" or "A" details.  How do I know whether Ubuntu is assigning /dev/cdrom or /dev/hdc to my cdrom?

Since it all works pretty well, I'm living without music on this box for a while while I puzzle it out.  (And, I'm going back to bed for now.)

Thanks for the ideas.

---

### Post by gerbman on 2006-06-07
[QUOTE=jmills]One thing I don't really get -being pretty new to Linux is how to identify the devices.  Click on the "computer" icon, and you can view the hard drives, and the CD ROMS and thumb drives, but they don't seem to have the Winblows "C" or "A" details.  How do I know whether Ubuntu is assigning /dev/cdrom or /dev/hdc to my cdrom?[/QUOTE]Open a terminal and type```
less /etc/mtab
```the output will tell you what devices are mounted where. For example, the line```
/dev/sda2 /home ext3 rw 0 0
```means that the device /dev/sda2 is mounted as my /home directory. You can do the same thing for CD-ROMS.

---

