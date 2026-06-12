---
title: "Manage mp3 collection on CDs"
date: 2006-11-03
forum: Multimedia &amp; Video
---

### Post by mkljun on 2006-11-03
Hi!

I was browsing the web to find an application that can manage mp3 collection
on CDs (browsing, searching, ...). I have around 30 CDs of mp3s with mixed music and I have a hard time finding things. 

Does anyone know a software that can scan CDs and storee  data about files on them? A close one was prokyon3 but it scans only hard drive directories. Any software that would manage any sort of files on cds would be fine.

Thx

lp mk

---

### Post by mkljun on 2006-11-06
I found a CD collection manager if anyone else  will be interested:
[http://sourceforge.net/projects/cdfly](http://sourceforge.net/projects/cdfly)

It's called CdFly and it looks promising.

lp mk

---

### Post by lqyjzmms on 2007-03-27
CdFly is a really nice little tool to catalogue your data CD / DVD collection.
Unfortunately, it is not included in the Ubuntu repositories and it is only distributed in a source code version for Linux.

I just compiled CdFly myself. I will try to sum up the steps I took to get an executable version of CdFly using edgy:

[LIST]
[*]Download the source code (either the .zip file or from the SVN repository of CdFly)
[*]```
sudo apt-get install build-essential libqt4-dev
```
those are the libraries and tools needed to compile CdFly
[*]Go to the directory containing the source code
[*]```
qmake-qt4
``` This will create a Makefile, but unfortunately it does not put all necessary libraries into it.
[*]Therefore, you will have to manually edit Makefile and add
```
-I/usr/include/qt4/QtSql
``` to INCPATH and
```
-lQtSql
``` to LIBS
[*]```
make
``` should now work
[*]```
./cdfly
``` will start CdFly
[/LIST]

I might have forgotten something, so post your problems here if it does not work for you the way I described it.

I would really appreciate a CdFly package in the Ubuntu repositories.

---

### Post by adam_kimber on 2007-04-22
> **lqyjzmms said:**
> This will create a Makefile, but unfortunately it does not put all necessary libraries into it.

I just compiled this on Feisty and the libraries were included in the Makefile. The compilation completed successfully. :D

---

### Post by mkljun on 2008-05-21
Unfortunally cdfly is not working in Hardy after the upgrade. I upgraded the system few days ago and cdfly chrashes with tons of errors in the console :(.


There is another post with all kinds of collection software:
[http://sudan.ubuntuforums.com/showthread.php?t=726902]("http://sudan.ubuntuforums.com/showthread.php?t=726902")

---

