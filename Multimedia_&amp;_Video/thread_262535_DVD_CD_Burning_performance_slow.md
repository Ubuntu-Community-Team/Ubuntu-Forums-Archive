---
title: "DVD/ CD Burning performance slow"
date: 2006-09-21
forum: Multimedia &amp; Video
---

### Post by GuiGuy on 2006-09-21
At the outset, let me apologise for the following rant- I am prompted to write out of frustration as I sit & wait for my Athlon XP based box with 1G RAM, 16X Pioneer and  Lite-on DVD burners burning a DVD at 1.68X speed :confused: 

This is an issue I have spent so much time on that I am ready to give up - all the advice given in these and other forums has been followed. I have tried tweaking all manner of settings. DMA is on, 32 I/O is on etc, etc. I have tried every bit of buring software I can get hold of (K3B, Nero Linux, GnomeBaker etc). I've changed burners and hard disks. Nothing seems to help.     

In fairness, I had the same unresolved problem with Suse and Mandrake distros so it doesn't seem to be Ubuntu specific but Linux generally.

Reading the complaints from others here and elsewhere about this issue it does seem that DVD burning at speed is not something Linux is especially good at. 

So, do I give up or is there a little bit of advice out there that I haven't tried? Or is a burning speed of ~1.6 as good as it gets with Linux?

---

### Post by dannyboy79 on 2006-09-22
I can't help yuou but I would ask you for your help in figuring out why I can't burn an xbox .iso file to a dvd using ubuntu and nero linux. I have also tried gnomebaker which doesn't work. It fails after it checks the image that was burned to the disk?? I always burn it at it's lowest setting, 4x. I have a I/O Magic DL DVD Burner. Can you help? I am not at home but will be later tonight so maybe we can get on xchat or something and we can go through it if you're willing to help me. I would also need instructions for setting up xchat because I never have irc'd before.

---

### Post by seanUSXIII on 2006-09-22
Make sure DMA (direct memory access) is enabled for the burner drive and your hard disks. [Here]("http://wiki.ubuntu.com/DMA") is a link to help enable it and explain what it does.

---

### Post by GuiGuy on 2006-09-22
> **seanUSXIII said:**
> Make sure DMA (direct memory access) is enabled for the burner drive and your hard disks. [Here]("http://wiki.ubuntu.com/DMA") is a link to help enable it and explain what it does.

Thanks for the reply, but as per my post above & with absolute certainty, DMA is enabled on all drives. It makes not a smidgeon on difference.

---

### Post by Biozid on 2007-01-20
I am having the same problem with the following hardware:

hda: ST3120026A, ATA DISK drive
hdc: SONY DVD RW DW-Q30A, ATAPI CD/DVD-ROM drive

Disk troughput can drop to <600kB/s when burning.

Running hdparm -tT /dev/hda gives following output:

 Timing cached reads:   1908 MB in  2.00 seconds = 953.68 MB/sec
 Timing buffered disk reads:   96 MB in  3.11 seconds =  30.87 MB/s

chipset is nforce2 ultra.

---

### Post by GuiGuy on 2007-01-31
> **GuiGuy said:**
> At the outset, let me apologise for the following rant- I am prompted to write out of frustration as I sit & wait for my Athlon XP based box with 1G RAM, 16X Pioneer and  Lite-on DVD burners burning a DVD at 1.68X speed :confused: 

This issue remains partially unresolved for me. Since upgrading to edgy the FIRST burn occurs at near max speed of hardware. Subsequent burns revert to about 1.6x 

I thought maybe it was hardware so I stopped using Linux for burning and used my WindowsXP box.

Anyway, last week I upgraded the linux PC with new hardware (AM2 dual core 3800+ 2G DDRII SATA etc). 

I have just tried a burn. The first one when fine- around 12X - 14X indicated on a 16X Pioneer burner, using Verbatim 16X DVD-R media, K3B software

The second burn? 1.25X to 1.6X

Settings are as they should be. I fail to see what else I can tweak.

Any ideas what else I can do? Back to Windows?

---

### Post by emarkay on 2007-01-31
Curious, as I plan to burn a DVD of my whole Linux volume shortly...

Any Gurus out there with answers?

---

### Post by jjacobs2 on 2007-02-16
This happens to me too but if I select data dvd project, make an image, then select a new project to burn the image it seems to work.  You can't verify that way though.  I hope they fix this soon.

---

