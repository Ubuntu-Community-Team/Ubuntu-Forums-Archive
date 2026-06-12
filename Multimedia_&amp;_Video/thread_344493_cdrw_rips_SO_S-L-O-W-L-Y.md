---
title: "cdrw rips SO S-L-O-W-L-Y"
date: 2007-01-23
forum: Multimedia &amp; Video
---

### Post by bradford72 on 2007-01-23
I just managed to get ubuntu up and (mostly) working about two days ago, and now that it works, I noticed that when I ripped a cd to my hdd it took a really long time (30 min for 64 MB) I am using a samsung cdr-rw is there a way to make juicebox or rhythmbox rip files from cd faster?

---

### Post by tommcd on 2007-01-23
The only thing I can think of is DMA. To check if DMA is on do <hdparm /dev/hdc> in terminal (assuming /dev/hdc is your drive, check in /etc/fstab).
If it says DMA is off, turn it on like this: <sudo hdparm -d1 /dev/hdc>
To enable DMA on bootup:
<gksudo gedit /etc/hdparm.conf>
Put this at the end of the file:

/dev/hdc {
dma = on
}

Just look at the examples in the hdparm.conf file.
Hope this helps.

---

### Post by bradford72 on 2007-01-24
> **tommcd said:**
> The only thing I can think of is DMA. To check if DMA is on do <hdparm /dev/hdc> in terminal (assuming /dev/hdc is your drive, check in /etc/fstab).

I'm not sure, but the output of hdparm /dev/hdc is> /dev/hdc:
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argumentwhen I look at hdparm.conf, I am intrigued by theese 2 lines> # -E cdrom speed
#cd_speed = 16And i'm wondering how they might come into play...like how I might form the command to set the speed of my cdrw, and where I would place it?

---

