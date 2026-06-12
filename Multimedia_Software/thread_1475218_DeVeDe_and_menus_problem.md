---
title: "DeVeDe and menus problem"
date: 2010-05-06
forum: Multimedia Software
---

### Post by stoppage on 2010-05-06
I'm using DeVeDe 3.6 on 8.04 to convert avi to dvd. Everything is o.k. until I try to choose a simple menu, then up pops  "Failed to create the DVD tree. maybe you don't have enough space."...which is rubbish.Has anybody got a solution to this please? Obliged

---

### Post by Y^2om&amp;#7sgP on 2010-05-08
I've started getting the same problem.  I cleared 45Gb from HDD (despite having 200Gb available) but still no joy.  Does anyone know how to fix this?

---

### Post by xc3RnbFO8P on 2010-05-08
I found this:
> As per my knowledge "DVD tree" is related to folder hierarchy and file name, May be u r trying to write very long folder structure or file name
try small one with single file or folder
> Don't use a fat32 partition for the output file. It's funny because devede says not to do so when it asks you for the output folder. Fat32 can only do 4GB files and a dvd is bigger than that, it is 4 and a half.

---

### Post by stoppage on 2010-05-08
Firstly..."Failed to create the DVD tree. maybe you don't have enough space." This is the only error message displayed no matter what error occurs
When "Add a menu" is deselected everything works fine so this error is somehow menu-related.

---

### Post by Y^2om&amp;#7sgP on 2010-05-09
I've now tried..

reformatting external 500Gb USB drive as Ext3, running Devede as sudo, removing the menu option tick mark, creating a Video CD.  All fail.

Can anyone shed light or suggest an alternate method of converting avi files to DVD format ..... please???

---

### Post by babarosa on 2010-05-09
Here [http://ubuntufromscratch.tuxfamily.org/](http://ubuntufromscratch.tuxfamily.org/) you find a very nice and comprehensive repo for hardy heron including devede v3.12c (you use v3.6). Maybe this problem is solved in the later version.

---

### Post by stoppage on 2010-05-09
> **babarosa said:**
> Here [http://ubuntufromscratch.tuxfamily.org/](http://ubuntufromscratch.tuxfamily.org/) you find a very nice and comprehensive repo for hardy heron including devede v3.12c (you use v3.6). Maybe this problem is solved in the later version.

Tried it. Problem remains

---

### Post by cloudscream on 2010-05-15
I encounter that error (the "disk space problem") everytime I use 10 or 11 titles. Try to limit the number of titles to 9.

---

### Post by alphacrucis2 on 2010-05-15
If you can't get around this problem, You could try qdvdauthor, which is what I use.

---

### Post by babarosa on 2010-05-15
Guys,

did you check in the settings, that your /tmp folder is located in a partition having enough free space?

My devede generates this hidden ini-file in my home folder:

video_format: pal
temp_folder:/var/tmp/
multicore:1
sub_language:EN (ENGLISH)
sub_codepage:ISO-8859-1

Additionally you could check that your user has access rights to this tmp folder.

Good luck,
Michael

---

### Post by Y^2om&amp;#7sgP on 2010-05-23
Have upgraded to Lucid Lynx which comes with PiTiVi.  Never used it before, but seems to do the job really well.

---

