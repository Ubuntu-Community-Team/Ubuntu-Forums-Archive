---
title: "create an ISO of a DVD in the shell...?"
date: 2009-04-07
forum: Multimedia Software
---

### Post by graysky on 2009-04-07
I know how to do this with K3B, but I'm wondering how I can make an iso of a DVD movie from the shell that I can then burn to a blank DVD-r?

Thanks!

---

### Post by estamand on 2009-04-07
You could just do "dd if=/dev/cdrom of=/cdrom_image.iso"

Change /dev/cdrom to your drive and cdrom_image.iso to the file and path were you want the iso file.

---

### Post by GeeZor on 2009-04-07
which is why Linux ROCKS!!!!!!!!

---

### Post by graysky on 2009-04-07
> **estamand said:**
> You could just do "dd if=/dev/cdrom of=/cdrom_image.iso"

Change /dev/cdrom to your drive and cdrom_image.iso to the file and path were you want the iso file.

I found this method via a google search, but it doesn't work w/ DVD movies for some reason... I know I have my DVDROM right.

---

### Post by danillo on 2009-04-07
Look up ```
man growisofs
```. I *think* it's possible to burn a iso to dvd with ```
growisofs -dvd-compat -Z /dev/dvd=image.iso
```

Oh, now I see. You want to create an iso. Well, never mind then...

---

### Post by andrew.46 on 2009-04-08
Hi graysky,

> **graysky said:**
> I found this method via a google search, but it doesn't work w/ DVD movies for some reason... I know I have my DVDROM right.

It will not work with most *commercial* dvd movies because they are copy protected. If it is legal in your country to backup your own movies you could use vobcopy + libdvdcss + libdvdread / mkisofs / growisofs:

Use vobcopy to rip the movie to your computer:

```
$ vobcopy -m
```

Change to the directory containing the movie files and run:

```
$ mkisofs -v -dvd-video -o ../movie_name.iso .
```

Then burn the iso to a blank disk:

```
$ cd ..
$ growisofs -dvd-compat -Z /dev/dvd=movie_name.iso
```

I believe in some countries you are not able to copy your own legally purchased disks, even for backup purposes, so just check this out before starting.

Andrew

---

### Post by kpkeerthi on 2009-04-08
Awesome. Thanks. Was looking for a commandline replacement for K9Copy.

---

### Post by andrew.46 on 2009-04-08
Hi kpkeerthi,

> **kpkeerthi said:**
> Awesome. Thanks. Was looking for a commandline replacement for K9Copy.

Bear in mind that Ubuntu does not actually use mkisofs, this is a symlink to a fork of Jörg Schilling's cdrtools. BTW you may be interested to know that I ripped off my own page for that example:

CD and DVD Writing from the Linux Command Line
[http://www.andrews-corner.org/burning.html](http://www.andrews-corner.org/burning.html)

And while I am pimping my own work perhaps you would like to try my most under-utilised guide which has yet to create a coaster for me:

Howto: Duplicate Audio CDs using cdrdao
[http://ubuntuforums.org/showthread.php?t=795181](http://ubuntuforums.org/showthread.php?t=795181)

I have a particular affection for cdrdao, it does an amazing job and the possibilities opened up with its commandline are truly amazing. And yes, I am a commandline junkie :-).

Andrew

---

