---
title: "unable to mount blank dvd"
date: 2007-08-07
forum: Multimedia &amp; Video
---

### Post by jamaas on 2007-08-07
When I put a blank dvd+RW in the drive I get an error message
"Cannot mount volume ... Invalid mount option when attempting to mount the volume"

Realise this should be self explanatory ... 

Dell d410 notebook, dvdrw is in docking station, reads cds and written dvds ok.

fstab has 
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0


and /dev/scd0 seems to work fine although get

sudo hdparm -iI /dev/scd0
Password:

/dev/scd0:
 HDIO_GET_IDENTITY failed: Invalid argument
 HDIO_DRIVE_CMD(identify) failed: Invalid argument

lspci has this in it

00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
        Subsystem: Dell Unknown device 018f
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at bfa0 [size=16]


Any suggestions how I can diagnose and fix this?  

Thanks

Jim

---

### Post by Ubukanuba on 2007-11-24
Same problem how did you fix it?

---

### Post by jamaas on 2007-11-25
Sorry mate, not been able to.  I think it may well just be a very dodgy cd drive, might need to replace it.  I've still not found a solution .... sorry

Jim

---

### Post by mikexgough on 2007-12-09
explain this..................my drive has the cant mount message on some media yet others it mounts as a blank dvd+-rw...............some are new and some are used...........some are even the same manufacturer...............there is no pattern to it?, cleaned the laser etc........I can still record on them though..........makes no sense

---

