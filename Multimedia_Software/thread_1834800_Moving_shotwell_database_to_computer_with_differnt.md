---
title: "Moving shotwell database to computer with differnt file paths"
date: 2011-08-28
forum: Multimedia Software
---

### Post by noteviljoe on 2011-08-28
I have copied all my photo's from my computer on to my laptop.

I wanted to retain all the shotwell additions so, following advice at [http://redmine.yorba.org/projects/shotwell/wiki/ShotwellFAQ](http://redmine.yorba.org/projects/shotwell/wiki/ShotwellFAQ), I copied the ~/.shotwell directory.

Unfortunately, I set my user name differently on the new laptop (as my full name father than short ver.). 

This means that the file paths are very slightly different on the laptop. i.e. rather than ~/home/username1/pictures/FolderA/example.jpg the photo will be at ~/home/username2/pictures/FolderA/example.jpg

Unfortunately this means that the shotwell database is now wrong and can't find the photo's.

I don't want to re-import the photo's because then (I imagine) they won't have all the changes I made using shotwell attached. (I already have tags set to write to photo files but think other info - rotation and event name etc. will be lost).

I've tried googling to no avail. Any help much appreciated.

---

### Post by handy on 2011-08-28
Changing your user name on the 2nd computer may be the easiest way out...

---

### Post by noteviljoe on 2011-08-28
Hold up, I spoke to soon.
It appears that Shotwell puts the files into 'missing files' but then scans whatever directory you have set up for it to watch files in (in my case the new laptops 'pictures' directory) and it can then alter its directory associating photo's (not sure is with same files name? or same attributes?) with its directory.

That is, it automatically changes directory for changed location.

Neat. Shotwell is the champ.

---

