---
title: "DVD Not Recognized"
date: 2010-08-12
forum: Multimedia Software
---

### Post by mainak_sen on 2010-08-12
I have recently installed Lucid on an Acer Aspire 5570Z laptop. It has an Optiarc DVD RW AD-7530A DVD-RAM writer. I am having trouble in playing video/movies on DVD.

When I am inserting a movie DVD, the drive is working (i.e. is busy) continuously but the disc is not being recognized and mounted. Disc Utility is showing "No Media Detected". 
The same DVD discs are playing OK in my desktop (running Hardy) and on another laptop (running Lucid).

Please note, however, that Audio and data CDs are playing/reading OK in the same drive. Even blank DVDs are being recognized and mounted OK.

I shall greatly appreciate if someone can help. Thanks in advance!

===========

*-cdrom
       description: DVD-RAM writer
       product: DVD RW AD-7530A
       vendor: Optiarc
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: EX31
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=busy

---

### Post by lidex on 2010-08-14
I recently ran into a similar issue when the disc had played just fine in a previous ubuntu release. Was a region setting.
Try installing this:
```
sudo apt-get install regionset
```
I set it to 0 and the disc plays now. Haven't tried much since, but no errors.
Reference:
[http://ubuntuforums.org/showthread.php?t=930164](http://ubuntuforums.org/showthread.php?t=930164)

---

