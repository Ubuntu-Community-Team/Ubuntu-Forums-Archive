---
title: "How to make .iso from directory (using command line)?"
date: 2007-07-02
forum: Multimedia &amp; Video
---

### Post by adt41287 on 2007-07-02
I ripped some dvd's onto my drive and i want to make and iso image from the directory that includes the vob files.  I've tried a couple different programs but all seem to spit back "this is a directory." Any other suggestions??

---

### Post by fumduck on 2007-07-02
have you tried devede? or avidemux

---

### Post by adt41287 on 2007-07-02
i know devede has a GUI... i want to use command line... im working on writing a script

---

### Post by SeattleUser on 2007-07-02
I used  mkisofs to create the iso from a directory created by dvdauthor.

---

### Post by diggity on 2007-07-02
To make an iso image from a directory, use the following:

```
mkisofs -o *iso_directory*/*iso_name*.iso *directory_of_movie*
```Example:
mkisofs -o /home/jdoe/myiso.iso /home/jdoe/myMovie

This will make an iso image of the files in /home/jdoe/myMovie and output myiso.iso in /home/jdoe

---

