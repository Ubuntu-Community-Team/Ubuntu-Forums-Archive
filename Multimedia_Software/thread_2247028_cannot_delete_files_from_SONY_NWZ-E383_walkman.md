---
title: "cannot delete files from SONY NWZ-E383 walkman"
date: 2014-10-05
forum: Multimedia Software
---

### Post by tomaasj on 2014-10-05
Hallo Anyone,

I can mount the SONY NWZ-E383 walkman, see the files, I can drag folders to the desktop, but I cannot delete files.

It says read permissions only.  Tried to right-click them but, it does not allow me to change the settings from read only.

How to proceed ?

Thanks in advance,

Tomaasj

---

### Post by yancek on 2014-10-05
Can't delete them from what?  After you copy them to your Desktop?  Or not from the mounted walkman?  If it is the latter, you nead to check the permissions where it is mounted.  So if you mount the walkman at /media/walkman, do:  ls -l /media/walkman and you will see the permissions.  You generally don't have write/delete permissions by default outside your /home/user directory.  You could gain access as root, using sudo.

---

### Post by Vladlenin5000 on 2014-10-05
> **yancek said:**
> You generally don't have write/delete permissions by default outside your /home/user directory.  You could gain access as root, using sudo.

Generally correct but this is a MP3 player... Usually, such players are just a FAT16/32 formatted flash memory, should be recognized as a mass storage device and shouldn't have permissions issues. The Sony NWZ-E383, however, doesn't "play by the rules" and can have some proprietary file system (or a common one with non-standard features). There must be a reason other then marketing for Sony to release special software (Windows/MAC only) for file transfer and there must be a very good technical reason for the explicit mention in the FAQs about it NOT being compatible with Windows "content transfer".

---

### Post by tomaasj on 2014-10-07
Hallo Yancek and Vladlenin5000,

Yancek:  I was able to drag and drop files from the walkman to my desktop.  But, I was not able to delete files from the mp3 player.  I was able to add but not remove files to regain memory space.  I tried gaining acces using sudo but to no avail.

Vladlenin5000: Out of pure frustration I formatted the drive.  After restarting the device I am now able to add and remove files.  So I guess I solved the problem.

Thanks for responding !

Tomaasj

---

