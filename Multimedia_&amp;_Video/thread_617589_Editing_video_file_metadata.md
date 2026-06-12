---
title: "Editing video file metadata"
date: 2007-11-19
forum: Multimedia &amp; Video
---

### Post by deresik on 2007-11-19
Hi all

Is there any way to edit/change file creation date and other metadata entries? I'm especially interested on changing it in video files, but knowledle about other files woudl be usefull. My purposes are that digikam sorts files by creation date, and after converting video (from 3gp to avi for example) my database is messed up.

---

### Post by erginemr on 2007-11-19
Hi there,

You can use the command line tool "touch" to change the creation date of files.

For the following sample file:
ls -l
-rw-r--r-- 1 user user 0 2007-11-19 22:13 sample.txt

If you issue:
touch --date "2006-01-01 11:00" sample.txt

You will get the following result:
ls -l
-rw-r--r-- 1 user user 0 2006-01-01 11:00 sample.txt

You can also use the touch command without a date argument to create new files:
touch new.file

---

