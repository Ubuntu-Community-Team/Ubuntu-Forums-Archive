---
title: "Burning WMV to DVD"
date: 2007-11-16
forum: Multimedia Production
---

### Post by Patriot1776 on 2007-11-16
Can mencoder be used to take a WMV file into a DVD burnable format?  I've got a couple large WMV files (350-400 MB) that I want to put on a DVD disc.  Also what programs would work best for burning a DVD from this format?

---

### Post by Patriot1776 on 2007-11-16
*sighs* Okay, if this IS NOT the right place for this, WHERE IS?  This is another question I've posted that's NOT gotten any repsonses.  I'm starting to wonder where the help is on this forum.

---

### Post by Patriot1776 on 2007-11-16
Somebody please delete this topic please.

---

### Post by Creative2 on 2007-11-18
:P hi 

install ffmpeg from MEDIBUNTU REPO

then use ffmpeg to convert wmv 

NB use a dvd-rw  and try this 

if you use pal (europe )

ffmpeg -i INPUT -target pal-dvd -aspect 4:3 OUTPUT

or if you prefer 

ffmpeg -i INPUT -target pal-dvd -aspect 16:9 OUTPUT

if you are in america and use NTSC format for your tv use this

ffmpeg -i INTPUT -target ntsc-dvd -aspect 4:3 OUTPUT 

or for 16.9 format

ffmpeg -i INTPUT -target ntsc-dvd -aspect 16:9 OUTPUT 

and if you want use a converter xD

use this 

[http://ubuntuforums.org/showthread.php?t=567016](http://ubuntuforums.org/showthread.php?t=567016)

---

### Post by stuartk on 2007-12-07
[QUOTE=Creative2;3793830]:P hi 

install ffmpeg from MEDIBUNTU REPO

then use ffmpeg to convert wmv 

NB use a dvd-rw  and try this 

if you are in america and use NTSC format for your tv use this

ffmpeg -i INTPUT -target ntsc-dvd -aspect 4:3 OUTPUT 



How about:


#!/bin/bash

# convert to mpeg 
ffmpeg -i $* -target ntsc-dvd -aspect 1.3333 temp.mpg

# create dvd filesystem with title and TOC and then remove temp mpeg file  
dvdauthor -o temp -t temp.mpg
dvdauthor -o temp -T
rm temp.mpg

# convert DVD filesystem into an iso file and remove temp directory
mkisofs -dvd-video -o DVD.iso temp
rm -rf temp

---

### Post by shivagit on 2008-04-15
That works great - Thanks

---

