---
title: "serpentine alternative"
date: 2007-10-25
forum: Multimedia Production
---

### Post by Smokeyone on 2007-10-25
As a newbie to Ubuntu I am very impressed but still stuck on trying to get Serpentine to make an audio cd.
Any alternative sugestions please, something  nice and easy.

---

### Post by orange2k on 2007-10-25
> **Smokeyone said:**
> As a newbie to Ubuntu I am very impressed but still stuck on trying to get Serpentine to make an audio cd.
Any alternative sugestions please, something  nice and easy.

Serpentine takes a lot of time to create audio CD-s, but it should work fine...
Much better solution to burning audio CD-s is K3b...

---

### Post by Smokeyone on 2007-10-26
Thanks for the suggestion. Having been trying out k3b and getting error messages 254 and use TAO writing mode. A google search found others had the same problem.
Any ideas please.......................

---

### Post by thelost on 2007-10-26
there are lots of burning programs for ubuntu. Why not try gnomebaker.

```
sudo apt-get install gnomebaker
```

---

### Post by Smokeyone on 2007-10-27
Will give a try and see what happens
Thanks very much

---

### Post by Smokeyone on 2007-10-29
Still no success but does this help.............


wodim: No write mode specified.
wodim: Asuming -tao mode.
wodim: Future versions of wodim may have different drive dependent defaults.
scsidev: '0,0,0'
scsibus: 0 target: 0 lun: 0
Linux sg driver version: 3.5.34
Wodim version: 1.1.2
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
TOC Type: 0 = CD-DA
atapi: 1
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'PIONEER '
Identification : 'DVD-RW  DVR-112D'
Revision       : '1.06'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0009 (CD-R)
Profile: 0x002B (DVD+R/DL) 
Profile: 0x001B (DVD+R) 
Profile: 0x001A (DVD+RW) 
Profile: 0x0016 (DVD-R/DL layer jump recording) 
Profile: 0x0015 (DVD-R/DL sequential recording) 
Profile: 0x0014 (DVD-RW sequential recording) 
Profile: 0x0013 (DVD-RW restricted overwrite) 
Profile: 0x0011 (DVD-R sequential recording) 
Profile: 0x0010 (DVD-ROM) 
Profile: 0x000A (CD-RW) 
Profile: 0x0009 (CD-R) (current)
Profile: 0x0008 (CD-ROM) 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1267712 = 1238 KB
FIFO size      : 12582912 = 12288 KB
4Speed set to 705 KB/s
9 Blocks remaining: 181789
Starting to write CD/DVD at speed   4.0 in real TAO mode for single session.
Last chance to quit, starting real write in 5 seconds.   4 seconds.   3 seconds.   2 seconds.   1 seconds.   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Starting new track at sector: 0
Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
CDB:  2A 00 00 00 09 99 00 00 1B 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 09 99 0E 00 00 00 00 64 00 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x64 Qual 0x00 (illegal mode for this track) Fru 0x0
Sense flags: Blk 2457 (not valid)

---

### Post by HMartinho on 2007-10-29
A couple of things:
 I didn't know K3b could run without KDE, is it possible to run it in Gnome?
Another really cool program is Brasero, I've been using it and so far no complaints, but I'll try gnomebaker also, ;).
By the way, gonna check into this K3B in gnome thingy, it would be nice if K3B worked in gnome.

Cheers.

---

### Post by orange2k on 2007-10-29
> **HMartinho said:**
> A couple of things:
 I didn't know K3b could run without KDE, is it possible to run it in Gnome?
Another really cool program is Brasero, I've been using it and so far no complaints, but I'll try gnomebaker also, ;).
By the way, gonna check into this K3B in gnome thingy, it would be nice if K3B worked in gnome.

Cheers.

It does work in Gnome, its probably the best burning app ever made...

---

