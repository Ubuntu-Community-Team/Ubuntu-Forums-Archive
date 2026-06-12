---
title: "Floppy Disk Drive Mounting Problems"
date: 2009-11-25
forum: Multimedia Software
---

### Post by carlalderson on 2009-11-25
I am running Ubuntu V9.0.  I go to places and click on Floppy Disk and the disk spins a few seconds and stops and nothing else happens.  I then go to Places and click on Computer and then click on Floppy Disk.  Will not mount the disk and a message appears as follows; Unable to mount - no media.  I do have a floppy disk in the drive.  I went and downloaded and installed KFloppy Formater.  I select the format option and it will not mount the disk and run.  It gives the following error message; internal error: device not correctly defined.
I then downloaded Dolphin and installed Dolphin.  Now the floppy is mounted.  I can transfer files on the floppy disk and transfer them off the disk all day long.  In Dolphin there is no option to format the disk.  KFloppy and also Disk Utility will not mount the floppy disk drive.  Can someone please tell me how to remedy this?
 [email]calderson@stny.rr.com[/email]

---

### Post by valvegrid on 2009-12-27
This post is a bit old, but you may have already found out how to do this, if you start KFloppy with sudo it will work.
If you want to mount the floppy then just open the terminal and type

[php]mount /media/floppy[/php]

that will mount the floppy on the desktop for you.

---

