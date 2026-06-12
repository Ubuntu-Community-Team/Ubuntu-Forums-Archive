---
title: "vlc - DVD stops playing at about 1hr+"
date: 2015-04-28
forum: Multimedia Software
---

### Post by pete38 on 2015-04-28
Everything works fine, and some disks are fine, others just stop at about 1 into the film...  I'm guessing (complete guess) that it has something to do with moving to the second layer, but this is supported by the drive.... I've tried multiple disks (films) and they suffer the same problem. Others play to the end of the film without a hitch...

CD-ROM drive supports MMC 3

                       Drive: /dev/sr1
Vendor                      : PIONEER 
Model                       : DVD-RW  DVR-215 
Revision                    : 1.06
Profile List Feature
    DVD+R Double Layer - DVD Recordable Double Layer
    DVD+R - DVD Recordable
    DVD+RW - DVD Rewritable
    DVD-R - Double-layer Jump Recording
    DVD-R - Double-Layer Sequential Recording
    Re-recordable DVD using Sequential Recording
    Re-recordable DVD using Restricted Overwrite
    Re-writable DVD
    disk Re-writable; with removable media
    Re-recordable DVD using Sequential recording
    Read only DVD
    CD-RW Re-writable Compact Disc capable
    Write once Compact Disc capable

Core Feature

Morphing Feature
    Operational Change Request/Notification not supported
    Synchronous GET EVENT/STATUS NOTIFICATION supported

Removable Medium Feature
    Tray type loading mechanism
    can eject the medium or magazine via the normal START/STOP command
    can be locked into the Logical Unit

Write Protect Feature

Random Readable Feature

Multi-Read Feature

CD Read Feature
    C2 Error pointers are supported
    CD-Text is supported

DVD Read Feature

Random Writable Feature

Incremental Streaming Writable Feature

Formattable Feature

Management Ability of the Logical Unit/media system to provide an apparently defect-free space. Feature

Restricted Overwrite Feature

DVD+RW Feature

DVD+R Feature

Rigid Restricted Overwrite Feature

CD Track at Once Feature

CD Mastering (Session at Once) Feature

DVD-R/RW Write Feature

Unknown code 33 Feature

CD-RW Media Write Support Feature

Hardware                                  : CD-ROM or DVD
Can eject                                 : Yes
Can close tray                            : Yes
Can disable manual eject                  : Yes
Can select juke-box disc                  : No

Can set drive speed                       : No
Can read multiple sessions (e.g. PhotoCD) : Yes
Can hard reset device                     : Yes

Reading....
  Can read Mode 2 Form 1                  : Yes
  Can read Mode 2 Form 2                  : Yes
  Can read (S)VCD (i.e. Mode 2 Form 1/2)  : Yes
  Can read C2 Errors                      : No
  Can read IRSC                           : Yes
  Can read Media Channel Number (or UPC)  : Yes
  Can play audio                          : Yes
  Can read CD-DA                          : Yes
  Can read CD-R                           : Yes
  Can read CD-RW                          : Yes
  Can read DVD-ROM                        : Yes

Writing....
  Can write CD-RW                         : Yes
  Can write DVD-R                         : Yes
  Can write DVD-RAM                       : Yes
  Can write DVD-RW                        : No
  Can write DVD+RW                        : No

---

### Post by blm-ubunet on 2015-05-04
Have you tried another player ?

I would try starting VLC with more verbose logging ( to file) & attempt to reproduce problem.
As a guess (don't use vlc cli):
vlc -v=2 > logfile.txt or vlc -vvv > logfile.txt

It is possible to dig deeper into verbose debug logging from libdvdread/nav but I would try another player first.

---

### Post by mc4man on 2015-05-04
Most likely a drive issue if problem disks are clean/not damaged  towards the outer edge. Can't image that drive is anywhere near new..

---

