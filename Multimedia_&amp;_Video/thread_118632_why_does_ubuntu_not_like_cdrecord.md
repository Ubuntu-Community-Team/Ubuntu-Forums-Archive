---
title: "why does ubuntu not like cdrecord"
date: 2006-01-17
forum: Multimedia &amp; Video
---

### Post by hca on 2006-01-17
I have serious problems writing cd's in ubuntu using cdrecord. 
Using any other distro i can do a cdrecord -scanbus and get:
Cdrecord-Clone 2.01a19 (i686-pc-linux-gnu) Copyright (C) 1995-2003 J\uffffrg Schilling
Using libscg version 'schily-0.7'
scsibus0:
        0,0,0     0) '  ATAPI ' '48X CDROM       ' '3.40' Removable CD-ROM
        0,1,0     1) 'LITE-ON ' 'DVDRW SOHW-1693S' 'KS09' Removable CD-ROM
        0,2,0     2) *
        0,3,0     3) *
        0,4,0     4) *
        0,5,0     5) *
        0,6,0     6) *
        0,7,0     7) *
hca@compaq5686:~$
  

but using ubuntu I get : 
hca@compaq5686:~$ cdrecord -scanbus
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

cdrecord: Warning: Running on Linux-2.6.12-10-386
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
cdrecord: No such file or directory. Cannot open '/dev/pg*'. Cannot open SCSI driver.
cdrecord: For possible targets try 'cdrecord -scanbus'. Make sure you are root.
cdrecord: For possible transport specifiers try 'cdrecord dev=help'.
cdrecord:
cdrecord: For more information, install the cdrtools-doc
cdrecord: package and read /usr/share/doc/cdrecord/README.ATAPI.setup .
hca@compaq5686:~$

would somebody PLEASE tell mi what do I do wring, OR what is bad with ubuntu

---

### Post by quonsar on 2006-01-17
```
sudo cdrecord -scanbus
```

---

### Post by hca on 2006-01-17
[QUOTE=quonsar]```
sudo cdrecord -scanbus
```[/QUOTE]

I DID try sudo before cdrecord -scanbus - this did not help!!! :

hca@compaq5686:~$ sudo cdrecord -scanbus
Password:
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

cdrecord: Warning: Running on Linux-2.6.12-10-386
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
cdrecord: No such file or directory. Cannot open '/dev/pg*'. Cannot open SCSI driver.
cdrecord: For possible targets try 'cdrecord -scanbus'.
cdrecord: For possible transport specifiers try 'cdrecord dev=help'.
cdrecord:
cdrecord: For more information, install the cdrtools-doc
cdrecord: package and read /usr/share/doc/cdrecord/README.ATAPI.setup .
hca@compaq5686:~$
hca@compaq5686:~$

---

