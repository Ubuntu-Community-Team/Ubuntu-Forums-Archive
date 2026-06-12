---
title: "Unable to record CDs"
date: 2007-03-24
forum: Multimedia &amp; Video
---

### Post by Ken Kaniff on 2007-03-24
Hi there, 

I'm hoping to get help with my problem. I run Ubuntu 6.06. After inslalling XFce grafical interface I'm unable to use my recorder.  

What's crazy, the recorder works if I want to burn music, NOT data or iso images.

Here's the error message I got when trying to burn a CD:

```
cdrecord: Warning: Running on Linux-2.6.15-28-386
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '/dev/hdd'
devname: '/dev/hdd'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted
cdrecord: Warning: using inofficial version of libscg (debian-0.8debian2 '@(#)scsitransp.c	1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
SCSI buffer size: 64512
cdrecord: Sorry, no CD/DVD-Recorder or unsupported CD/DVD-Recorder found on this target.
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

TOC Type: 1 = CD-ROM
Using libscg version 'debian-0.8debian2'.
Driveropts: 'burnfree'
atapi: 1
Device type    : Removable CD-ROM
Version        : 0
Response Format: 1
Vendor_info    : 'LITEON  '
Identifikation : 'CD-ROM LTN526   '
Revision       : 'YH0X'
Device seems to be: Generic mmc CD-ROM.
Current: 0x0000
Profile: 0x0008 

```

Below another error I got when trying to erase a CD RW disk.

```
cdrecord: Warning: Running on Linux-2.6.15-28-386
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '/dev/cdrom'
devname: '/dev/cdrom'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted
Using libscg version 'debian-0.8debian2'.
cdrecord: Warning: using inofficial version of libscg (debian-0.8debian2 '@(#)scsitransp.c      1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
Device type    : Removable CD-ROM
Version        : 0
Response Format: 1
Vendor_info    : 'LITEON  '
Identifikation : 'CD-ROM LTN526   '
Revision       : 'YH0X'
Device seems to be: Generic mmc CD-ROM.
cdrecord: Sorry, no CD/DVD-Recorder or unsupported CD/DVD-Recorder found on this target.

```

All comments are welcome. Thanks.

---

### Post by Barney on 2007-04-26
Likewise here. Unable to burn data cd; very similar, probably same error message.

I have been able to burn in the past with the same equipment - suspect some update interfered(?).

Help?

---

### Post by Ken Kaniff on 2007-04-27
I didn't solve my issues [there more then the one above] and switched to OpenSUSE, which works like a charm. 

Nothing against Ubuntu. Only, too bad that my country's forums don't treat people seriously. If I got any answers they were: "Browse the forum - everything's here."

Good luck dealing with your issue.

---

