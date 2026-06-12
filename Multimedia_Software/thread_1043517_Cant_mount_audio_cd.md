---
title: "Cant mount audio cd"
date: 2009-01-18
forum: Multimedia Software
---

### Post by mick222 on 2009-01-18
I am trying to rip some audio cd's  to my hard drive in Intrepid 
most will not mount . I get an error /dev/scd0 does not contain audio files.I  have attached the output of lshw -c disk which correctly shows my cd dvd drive.
[PHP]  *-cdrom
       description: DVD writer
       product: DVD_RW ND-2510A
       vendor: _NEC
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 2.96
       serial: [_NEC    DVD_RW ND-2510A 2.9604062400
       capabilities: removable audio cd-r cd-rw dvd dvd-r
       configuration: ansiversion=5 status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom
[/PHP]

---

### Post by mick222 on 2009-01-20
Tried in Jaunty still cannot rip cd's ., could this be a fault with my cd dvd player.

---

### Post by mc4man on 2009-01-20
You haven't mentioned how your trying to rip. Your lshw does indicate media in the drive (status=ready), no filesystem (what you expect from an audio cd) and a logical name in the media listing of /dev/cdrom (also what an audio cd would show (also true for blank media.

Why don't you take a look in home folder (edit -> show hidden files) -> .gvfs and see if there's a folder 'cdda mount on /dev/scd0' and if so can you see the .wav's inside.

If all this exists point your ripper to /dev/cdrom

If nothing is inside of .gvfs then maybe there is a problem with the drive.

---

### Post by mick222 on 2009-01-20
.gvfs is empty still shows up as blank disc . I was using rhythmbox to rip also tried sound juicer.It must be the drive.
Should there be anything in that folder when there is no ddisc in the drive.

---

### Post by mc4man on 2009-01-20
> Should there be anything in that folder when there is no disc in the drive.
No, only audio cd's will show up there (I thought I remember something else going there in intrepid beta, but atm only audio cd's

---

### Post by mick222 on 2009-01-21
ok thx guess ibetter go buy a new dvd writer

---

