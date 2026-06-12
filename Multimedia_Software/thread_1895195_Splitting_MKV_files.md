---
title: "Splitting MKV files"
date: 2011-12-14
forum: Multimedia Software
---

### Post by Azrael84 on 2011-12-14
Hi,

I have a large MKV movie, I want to put this on my usb drive, but of course fat32 only allows 4GB so I can't copy it over without error, hence I want to split this MKV into two parts or more.

Could anyone tell me how to do this? I've tried avidemux but I get "H.264 detected" errors, whatever that is...

thanks

---

### Post by SeijiSensei on 2011-12-14
You could probably do this with **mencoder**:

```
mencoder -o partone.mkv -endpos 3600 -ovc copy -oac copy movie.mkv
mencoder -o parttwo.mkv -ss 01:00:00 -ovc copy -oac copy movie.mkv
```

The first command copies the first hour of the film; the second copies the remainder.  You might actually want to start the second part a bit early to ensure complete coverage; use "00:58:00" to start two minutes before the end of part one.

---

### Post by TiberiusT on 2011-12-14
[http://www.bunkus.org/videotools/mkvtoolnix/](http://www.bunkus.org/videotools/mkvtoolnix/)

T

---

### Post by andrew.46 on 2011-12-14
As Tiberius has mentioned the easiest way may be with mkvtoolnix, I attach a screenshot to show the gui options.

---

### Post by coldraven on 2011-12-14
I have a 8GB Super-Talent USB stick and a 1TB Samsung Story USB drive.
I formatted them both to NTFS with gparted, problem solved :)

---

### Post by Azrael84 on 2011-12-15
Thanks for the help, mkvmerge did the job perfectly...

---

