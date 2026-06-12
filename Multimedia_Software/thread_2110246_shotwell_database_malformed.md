---
title: "shotwell database malformed"
date: 2013-01-29
forum: Multimedia Software
---

### Post by martinyt on 2013-01-29
My shotwell database is malformed and can't find a solution for it. 

The problem is that a lot of pictures won't show up in shotwell (but videos do) no error message.

I had a look at:
[http://askubuntu.com/questions/58295/how-can-i-restore-a-corrupted-shotwell-db](http://askubuntu.com/questions/58295/how-can-i-restore-a-corrupted-shotwell-db)

so I tried restoring the database (from photo.db.back) without any luck - it has the same issues.

The pragma integrity_check gives:

sqlite> pragma integrity_check;
*** in database main ***
Page 1090: btreeInitPage() returns error code 11
On tree page 996 cell 6: Child page depth differs
On tree page 996 cell 7: Child page depth differs
Page 29: btreeInitPage() returns error code 11
On tree page 27 cell 2: Child page depth differs
On tree page 27 cell 3: Child page depth differs
Error: database disk image is malformed

I run ubuntu 12.10 and shotwell 0.13.1. I am missing about two year with photos (I have the photos of course)

Any ideas to fix this? Or suggestion to other photo organizer which does not use sqlite ;-)

---

### Post by eric-yorba on 2013-01-29
Yikes, I'd be worried about this one if I were you.  There's really no way both the main database and the automatic backup should be corrupt, so this could indicate a larger problem.

Have you checked your disk for errors?

---

### Post by martinyt on 2013-02-01
Thanks for the answer! 

I ran a 
sudo touch /forcefsck
 and rebooted, but the disk's seems ok. no errors.

Is there a shotwell forum I could ask?

---

### Post by eric-yorba on 2013-02-01
Best place to ask would be the mailing list.  Info is up here on the Shotwell wiki:
[http://redmine.yorba.org/projects/shotwell/wiki#Mailing-list](http://redmine.yorba.org/projects/shotwell/wiki#Mailing-list)

---

