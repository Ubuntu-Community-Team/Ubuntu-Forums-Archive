---
title: "DVD from Australia Hates Laptop from Bulgaria"
date: 2011-03-24
forum: Multimedia Software
---

### Post by bruc33ef on 2011-03-24
My Lenovo 3000/N200 laptop combo drive (HL-DT-ST) won't acknowledge DVDs from Australia that state they can be played by NTSC or PAL drives and are set to Region-0.  I downloaded libdvdcss2 and libdvdread4 and every possible codec from Medibuntu.  I messed with VLC.  I tried regionset.  I'm convinced I need to flash the drive for RPC-1 or to set Region 0 (which regionset won't do), but the only utilities available run only in Windows.  Is there a way to flash from Ubuntu?  Or, are there flashing utilities that work from Ubuntu?  I tried using a Windows Live CD but that won't work.  Wine won't do it.  I certainly don't want to install Windows again just to flash the combo drive.  Any help would be greatly appreciated!


Regionset tells me the following (with a readable DVD from the US in the drive):

=======================
regionset version 0.1 -- reads/sets region code on DVD drives
Current Region Code settings:
RPC Phase: II
type: SET
vendor resets available: 4
user controlled changes resets available: 4
drive plays discs from region(s): 1, mask=0xFE[/SIZE]
=======================

'lshw -C' tells me the following:

=================================
*-cdrom
       description: DVD-RAM writer
       product: DVDRAM GMA-4082N
       vendor: HL-DT-ST
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       logical name: /media/Data disc (17 Oct 10)
       version: ED01
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500 state=mounted status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom
          logical name: /media/Data disc (17 Oct 10)
          configuration: mount.fstype=iso9660 mount.options=ro,nosuid,nodev,rela
time,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500 state=mounted

======================================

---

