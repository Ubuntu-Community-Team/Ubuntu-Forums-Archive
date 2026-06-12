---
title: "Lucid does not work right with dvd-rw media"
date: 2010-06-04
forum: Multimedia Software
---

### Post by glaubersm on 2010-06-04
When I put a blank rewritable media in the drive no icon appears on the desktop and if I try to burn an iso image, for example, with the option that the right finds no brasero asks to insert media and some in the unit. Another problem is that brasero leaves the locked drawer of the unit for a few minutes after erase dvd-rw media. Is there any solution to these two problems?

---

### Post by zenuna on 2010-06-04
I am having the same problems.  Have installed other software like AcidRip, DeVeDe,dvd rip, GnomeBaker, kb3.  I cannot successfully burn anything on a DVD/RW.  This is very aggravating, but the most annoying is the DVD getting stuck in the drive.  Regular Cd's will work fine and eject whenever I need them to.  But DVD's... sometimes I have to reboot to get the drive to open.  

Anyone else having these problems?  Or know how to correct?

---

### Post by glaubersm on 2010-06-07
Any solution?

---

### Post by mail.prabal on 2010-06-17
i am having the same problem...when the disk is empty,it doesnt show....when it has some data,it is detected....but if i erase the disk,again it dissapears from my system....

Please help

---

### Post by ghostborg on 2010-06-20
You could try NeroLinux4, I think it has a trail period.
I found trusty ol' K3b to have a few issues, for me with Lucid AMD64.
Brasero could not do Multisession +R media for me.


Nero has it's faults too.
I had a problem with Nero and Multisession and found the following solution from another forum:
Many of you experiences issues with Nero Linux 4 when continuing a multisession disc. Apparently, Nero Linux 4 is looking for some shared libs in the wrong folder, so, of course it is _NEVER_ possible to continue a multisession disc.

This issue will of course be fixed in the next release (don't ask for a date ), but you can use the following trick to make it work for now. As root,

    * - Go in /usr/lib/nero (/usr/lib64/nero for the 64-bit version)
    * - Once you are there, copy the files libISOFS.so and libUDFImporter.so to the /usr/lib (/usr/lib64 for the 64-bit version).

This should let you use the multisession features of Nero Linux 4.
Also remember to manually delete these 2 files before you uninstall or upgrade the nero linux package.

---

### Post by postenga on 2010-06-30
> **ghostborg said:**
> You could try NeroLinux4, I think it has a trail period.
I found trusty ol' K3b to have a few issues, for me with Lucid AMD64.
Brasero could not do Multisession +R media for me.


Nero has it's faults too.
I had a problem with Nero and Multisession and found the following solution from another forum:
Many of you experiences issues with Nero Linux 4 when continuing a multisession disc. Apparently, Nero Linux 4 is looking for some shared libs in the wrong folder, so, of course it is _NEVER_ possible to continue a multisession disc.

This issue will of course be fixed in the next release (don't ask for a date ), but you can use the following trick to make it work for now. As root,

    * - Go in /usr/lib/nero (/usr/lib64/nero for the 64-bit version)
    * - Once you are there, copy the files libISOFS.so and libUDFImporter.so to the /usr/lib (/usr/lib64 for the 64-bit version).

This should let you use the multisession features of Nero Linux 4.
Also remember to manually delete these 2 files before you uninstall or upgrade the nero linux package.





I tried this steps ([http://club.myce.com/](http://club.myce.com/)) and work for me about muitsessions burns.. but brasero and nero linux 4 can't copy a whole cd or dvd. i've tried the oficial suport and :

Did you already check if the drive file permissions are set correctly?
Please check up with our Nero Linux manual if your optical devices are configured correctly for usage with Nero Linux.

You can download the Nero Linux manual here:
[http://www.nero.com/eng/support-linux3-manuals.html](http://www.nero.com/eng/support-linux3-manuals.html)
Please refer to the chapter 14.1.3 – Advanced system requirements

i tried that steps too ad the problem already bug me. I think it's a lucid lynx issue...

---

