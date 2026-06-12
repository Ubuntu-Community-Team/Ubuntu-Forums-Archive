---
title: "ubuntu 9.10 problem ripping VCD with vcdxrip - assertion failed error"
date: 2010-03-13
forum: Multimedia Software
---

### Post by venkat_kotra on 2010-03-13
Hi I am trying to rip VCD using vcdxrip.
below is what i did:

devkit-disks --mount /dev/scd0
vcdxrip -i /dev/scd0

>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
++ WARN: XA signature not found in ISO9660's system use area; ignoring XA attributes for this file entry.
++ WARN: XA signature not found in ISO9660's system use area; ignoring XA attributes for this file entry.
>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>

vcd-info -i /dev/scd0
>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
-------------------------------------------------------------------------------
vcd-info - GNU VCDImager - (Super) Video CD Report
$Id: vcd-info.c,v 1.23 2005/05/08 08:42:09 rocky Exp $

++ WARN: XA signature not found in ISO9660's system use area; ignoring XA attributes for this file entry.
Source: image file `/dev/scd0'
Image size: 327582 sectors
VCD 1.1 detected
-------------------------------------------------------------------------------
ISO9660 primary volume descriptor
 ID: `CD001'
 version: 1
 system id: `CD-RTOS CD-BRIDGE'
 volume id: `TOX_VCD'
 volumeset id: `'
 publisher id: `TERAOPTIX'
 preparer id: `TAN KAY HING'
 application id: `EASY CD CREATOR 4.0 (140) COPYRIGHT (C) 1996-1999 ADAPTEC, INC.'
 ISO size: 31 blocks (logical blocksize: 2048 bytes)
 XA marker present: yes
-------------------------------------------------------------------------------
ISO9660 filesystem dump
 root directory in PVD set to LSN 20

++ WARN: XA signature not found in ISO9660's system use area; ignoring XA attributes for this file entry.
 /:
  d d---1xrxrxr 0 0 [fn 00] [LSN     20]      2048  .
  d d---1xrxrxr 0 0 [fn 00] [LSN     20]      2048  ..
  d d---1xrxrxr 0 0 [fn 00] [LSN     21]      2048  CDDA
  d d---1xrxrxr 0 0 [fn 00] [LSN     22]      2048  CDI
  d d---1xrxrxr 0 0 [fn 00] [LSN     23]      2048  EXT
  d d---1xrxrxr 0 0 [fn 00] [LSN     26]      2048  MPEGAV
  d d---1xrxrxr 0 0 [fn 00] [LSN     24]      2048  SEGMENT
  d d---1xrxrxr 0 0 [fn 00] [LSN     25]      2048  VCD

++ WARN: XA signature not found in ISO9660's system use area; ignoring XA attributes for this file entry.
 /CDDA/:
  d d---1xrxrxr 0 0 [fn 00] [LSN     21]      2048  .
  d d---1xrxrxr 0 0 [fn 00] [LSN     20]      2048  ..

++ WARN: XA signature not found in ISO9660's system use area; ignoring XA attributes for this file entry.
 /CDI/:
  d d---1xrxrxr 0 0 [fn 00] [LSN     22]      2048  .
  d d---1xrxrxr 0 0 [fn 00] [LSN     20]      2048  ..

++ WARN: XA signature not found in ISO9660's system use area; ignoring XA attributes for this file entry.
 /EXT/:
  d d---1xrxrxr 0 0 [fn 00] [LSN     23]      2048  .
  d d---1xrxrxr 0 0 [fn 00] [LSN     20]      2048  ..

++ WARN: XA signature not found in ISO9660's system use area; ignoring XA attributes for this file entry.
 /MPEGAV/:
!ASSERT: file vcd-info.c: line 934 (_dump_fs_recurse): assertion failed: (entlist != NULL)
Aborted
>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>


How can I rip the VCD
how ever I can play the vcd using mplayer
mplayer vcd://2

mplayer vcd://1 does not work and gives the below output
>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
MPlayer SVN-r29934-4.4.1 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing vcd://1.
track 01:  adr=1  ctrl=6  format=2  00:02:00  mode: 1
track 02:  adr=1  ctrl=6  format=2  00:12:00  mode: 1


Exiting... (End of file)
>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>

is this somthing to do with the actual problem.

thanks and regards
venkat

---

### Post by venkat_kotra on 2010-03-13
solved the problem of ripping by using mplayer 

[http://ubuntuforums.org/showthread.php?t=1097791](http://ubuntuforums.org/showthread.php?t=1097791)

but vcdxrip still doesnt work..

thanks
venkat

---

### Post by aero13972486 on 2013-01-30
Use K3B. It used vcdxrip but handles things like finding the right drive.

---

### Post by shajalalmia2 on 2013-01-30
Great post,I have carefully read your cortical description &
 I am interested to take your cortical.i am very interested for your details
thank you for your biutiful articals

---

### Post by overdrank on 2013-01-30
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

