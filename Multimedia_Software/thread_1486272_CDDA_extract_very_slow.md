---
title: "CDDA extract very slow"
date: 2010-05-17
forum: Multimedia Software
---

### Post by tsh on 2010-05-17
Not sure where the problem is. I have a new sata dvd writer from LG, and it won't extract digital audio at much more than 1x, or maybe 3x with -Z. I can write to it OK, so I'm guessing DMA is working properly.

>cdparanoia -A
cdparanoia III release 10.2 (September 11, 2008)

Using cdda library version: 10.2
Using paranoia library version: 10.2
Checking /dev/cdrom for cdrom...
	Testing /dev/cdrom for SCSI/MMC interface
		SG_IO device: /dev/sr0

CDROM model sensed sensed: HL-DT-ST DVDRAM GH22NS50 TN02 
 

Checking for SCSI emulation...
	Drive is ATAPI (using SG_IO host adaptor emulation)

Checking for MMC style command set...
	Drive is MMC style
	DMA scatter/gather table entries: 1
	table entry size: 131072 bytes
	maximum theoretical transfer: 55 sectors
	Setting default read size to 27 sectors (63504 bytes).

Verifying CDDA command set...
	Expected command set reads OK.

Attempting to set cdrom to full speed... 
	drive returned OK.

=================== Checking drive cache/timing behavior ===================

Seek/read timing:
	[56:52.10]:   73ms seek, 1.55ms/sec read [8.6x]                 
	[50:00.00]:   62ms seek, 1.66ms/sec read [8.0x]                 
	[40:00.00]:   96ms seek, 1.80ms/sec read [7.4x]                 
	[30:00.00]:   84ms seek, 1.99ms/sec read [6.7x]                 
	[20:00.00]:   85ms seek, 2.27ms/sec read [5.9x]                 
	[10:00.00]:  117ms seek, 2.69ms/sec read [5.0x]                 
	[00:00.00]:  144ms seek, 3.47ms/sec read [3.8x]                 

Analyzing cache behavior...
	Approximate random access cache size: 16 sector(s)               
	Drive cache tests as contiguous                           
	Drive readahead past read cursor: 234 sector(s)                
	Cache tail cursor tied to read cursor                      
	Cache tail granularity: 1 sector(s)                      
	        Cache read speed: 0.13ms/sector [101x]
	        Access speed after backseek: 3.42ms/sector [3x]
	Backseek flushes the cache as expected

Drive tests OK with Paranoia.

---

### Post by BobvanderPoel on 2010-09-04
Any success? I've got a similar (same) drive:

ATAPI CD-ROM, with removable media
	Model Number:       HL-DT-ST DVDRAM GH22NS50                
	Serial Number:      K00998K1011         
	Firmware Revision:  TN01    
	Transport:          Serial, ATA8-AST, SATA 1.0a, SATA II Extensions, SATA Rev 2.5, SATA Rev 2.6

I find that a CD I can rip in about 5 minutes on my older PATA Sony drive takes 4 to 5 times a long on the newer one. I've sort of given up on searching for answers on this ... for the cost of a drive I may just grab another Sony.

But, before I do ... I'm sure it's a "little thing" and really would like to resolve it.

---

