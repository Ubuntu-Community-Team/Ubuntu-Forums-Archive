---
title: "Not been able to blank a dvd+rw with Brasero (U-7.10)"
date: 2009-03-27
forum: Multimedia Software
---

### Post by kruegger on 2009-03-27
I've tried to blank a dvd+rw with Brasero and Gnomebaker. After reading the log output, I wanted to run cdrecord from command line and it shed the following:

aser@ubuntu:~$ cdrecord driver=mmc_dvdplusrw blank=fast
Cdrecord-ProDVD-ProBD-Clone 2.01.01a33 (i686-pc-linux-gnu) Copyright (C) 1995-2007 J&#65533;rg Schilling
Linux sg driver version: 3.5.34
Using libscg version 'schily-0.9'.
No target specified, trying to find one...
Using dev=1,0,0.
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'ASUS    '
Identifikation : 'DRW-1814BL      '
Revision       : '1.13'
Device seems to be: Generic mmc2 DVD-R/DVD-RW/DVD-RAM.
Using generic SCSI-3/mmc-3 DVD+RW driver (mmc_dvdplusrw).
Driver flags   : NO-CD DVD MMC-3 SWABAUDIO BURNFREE 
Supported modes: PACKET SAO LAYER_JUMP
Starting to write CD/DVD/BD at speed 4 in real BLANK mode for single session.
Last chance to quit, starting real write    0 seconds. Operation starts.
cdrecord: **[B][COLOR="Lime"][COLOR="#00ff00"]Cannot blank with non Ricoh based drive.[/COLOR][/COLOR]**[/B]
cdrecord: Cannot blank disk, aborting.
cdrecord: Some drives do not support all blank types.
cdrecord: Try again with cdrecord blank=all.

Tried the all option and:
cdrecord: [COLOR="#00ff00"]Cannot blank with non Ricoh based drive[/COLOR].
cdrecord: Cannot blank disk, aborting.

¿Does this mean that blanking is not supported in cdrecord (nor Brasero nor Gnomebaker) for dvd+rw unless one has a Ricoh optical drive?. If so,
¿Is there a workaround?. I've been through the cdrecord and genisoimage man pages but it's too thick for me](*,).

My Ubuntu is Gutsy Gibbon.

Thank you, guys.):P

---

