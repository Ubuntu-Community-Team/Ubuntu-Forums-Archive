---
title: "can't burn cd's at all"
date: 2006-10-30
forum: Multimedia &amp; Video
---

### Post by redwolf963 on 2006-10-30
I am going crazy with this problem.

When i try to burn an iso with gnomebaker,k3b,graveman or xcdrecord.I get the same error message:
            
            libnotify-Message: Unable to get session bus: No reply within specified time

** (gnomebaker:6903): WARNING **: gbcommon_close_temp_file - Temporary file desc riptor [/tmp/GnomeBaker-root/gnomebaker-2YAppx] could not be closed

** (gnomebaker:6903): WARNING **: devices_is_disk_inserted - ioctl failed

** (gnomebaker:6903): WARNING **: devices_eject_disk - Error opening device h\u0 013[\u0008/hdc

** (gnomebaker:6903): CRITICAL **: dbus_g_proxy_connect_signal: assertion `DBUS_ IS_G_PROXY (proxy)' failed

** (gnomebaker:6903): CRITICAL **: dbus_g_proxy_connect_signal: assertion `DBUS_ IS_G_PROXY (proxy)' failed

** (gnomebaker:6903): CRITICAL **: dbus_g_proxy_call: assertion `DBUS_IS_G_PROXY  (proxy)' failed

** (gnomebaker:6903): CRITICAL **: dbus_g_proxy_call: assertion `DBUS_IS_G_PROXY  (proxy)' failed
  
 I can't decipher what this means.
Tried as root,checked my groups,everything I can think of to no avail.

   Please help!

 redwolf963
 By the way,I am using Dapper.

---

### Post by ceargle on 2006-10-30
In Dapper, I've always just right-clicked the .iso file and selected Burn to Disc...

If that doesn't work maybe someone else can offer a better solution!

Hope it works for you.

---

### Post by redwolf963 on 2006-10-30
No,that doesn't work either.
I even reinstalled cdrecord.Still nothing.

So,next I tried a different cd-burner.Same problem.
Tried gconf-editor and set burnfree.

Nothing.Checked that my /dev files pointed to the right place.

I'm at a total loss.

  redwolf963

---

### Post by redwolf963 on 2006-10-30
Here is the output from gnomebaker:

cdrecord: No write mode specified.
cdrecord: Asuming -tao mode.
cdrecord: Future versions of cdrecord may have different drive dependent defaults.
cdrecord: Continuing in 5 seconds...
cdrecord: Warning: Running on Linux-2.6.15-27-386
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '/dev/hdd'
devname: '/dev/hdd'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
cdrecord: Warning: using inofficial version of libscg (debian-0.8debian2 '@(#)scsitransp.c	1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
SCSI buffer size: 64512
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

TOC Type: 3 = CD-ROM XA mode 2
Using libscg version 'debian-0.8debian2'.
Driveropts: 'burnfree'
atapi: 1
Device type    : Removable CD-ROM
Version        : 0
Response Format: 1
Vendor_info    : 'MITSUMI '
Identifikation : 'CD-ROM FX600S !B'
Revision       : 'P01 '
Device seems to be: Philips CDD-522.
Using driver for Philips CDD-522 (philips_cdd522).
Driver flags   : 
Supported modes: TAO
FIFO size      : 4194304 = 4096 KB
cdrecord: Drive needs to reload the media to return to proper status.
cdrecord: Success. philips medium load/unload: scsi sendcmd: no error
CDB:  E7 00 00 00 00 00 00 00 01 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 06 00 00 00 00 20 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x20 Qual 0x00 (invalid command operation code) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.001s timeout 40s
cdrecord: Cannot eject media.

It then locks up.

redwolf963

---

