---
title: "DVD is no-go, have no /dev/hdc"
date: 2007-10-17
forum: Multimedia &amp; Video
---

### Post by darenw on 2007-10-17
i'm trying to play DVDs on my main machine, running Ubuntu 7.04.  The CD/DVD is an LTN486S.    i'm pretty sure my multimedia software is okay, with libdvdcss.so installed and all that stuff okay, according to other forum threads etc.   I'm suspecting problems with udev or kernel module trouble or something at that level.   The drive is physically okay, afik, since i've been using it to boot up knoppix and ubuntu CDs only a month ago.  

There is no /dev/dvd and if i manually create one as a symlink to /dev/hdc, nothing good happens since there's no /dev/hdc.    Running 
  dmesg |grep -i dvd    
reports this:
  [17179576.692000] hdc: LTN486S, ATAPI CD/DVD-ROM drive

i assume this means that the CD/DVD drive should appear as /dev/hdc.    The only /dev/hd* or /dev/sd* are other devices which all function fine.  

/proc/version says:
 Linux version 2.6.17-12-386 (root@terranova) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 Mon Jul 16 19:35:45 UTC 2007 (Ubuntu 2.6.17-12.39-386)

---

### Post by darenw on 2007-10-17
update - i'm not getting anything to work on that drive, actually,  not even a plain ol' ordinary data CD.     seems to be deeper trouble than anything related to multimedia/DVD.   

dmesg reports also this about hdc:
 ide1: I/O resource 0x376-0x376 not free.
[17179574.376000] hdc: ERROR, PORTS ALREADY IN USE

googling turns up others with similar trouble but no one seems to know what the real problem is.

---

