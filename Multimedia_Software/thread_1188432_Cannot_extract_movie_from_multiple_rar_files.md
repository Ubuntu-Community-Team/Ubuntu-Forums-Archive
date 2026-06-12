---
title: "Cannot extract movie from multiple rar files"
date: 2009-06-15
forum: Multimedia Software
---

### Post by Lorenz on 2009-06-15
Hi guys,
I have the following problem:
I have downloaded a movie and it came in about 50 separate .rar files. 
In previous versions of Ubuntu, I just clicked on one and it would automatically use all the .rar files to create one .avi file. This time around, it still displays that the finaly file should be 700MBs, but when I click on extract it only creates a file of 14MB. I cannot find out what to do, to extract the whole movie. Any help is gladly appreciated. This is either a quite big bug or I am missing some package. Thank you!

And for the record, it's not important how I obtained the copy of this movie ;)

---

### Post by Lorenz on 2009-06-16
anyone please?

---

### Post by stinger30au on 2009-06-16
the .rar file(s) are corrupt

when you d/l this stuff i suggest you do not use any download accelerators, just let the web browser download it its self

---

### Post by Lorenz on 2009-06-16
thank you for the answer!
I downloaded the files via torrent (deluge). I'll make a check to see if I am missing some KBs. But it's strange, this has never happened to me and now it occured already twice - so I suspected there might be a bug involved.

---

### Post by CHW on 2009-06-16
Hello,

I also have sometimes strange archive file behaviour.
Because of that I often use the console to extract files.

cd to file location and use:
rar x name_of_file

You have also the possibility to repair corrupted files:
rar r name_of_file
The file is then stored as rebuilt.name_of_file (or something similar, I can't remember exactly...).
Hope that helps.

Regards,
CHW

---

### Post by Lorenz on 2009-06-16
Hi, so I have checked the rar files and they are not broke. This seems to be a bug. Has anyone recently tried to unpack a file that was split in several rar files?

---

### Post by Lorenz on 2009-06-16
thanks to CHW's comment, I have found the solution.
I had to install the package "rar" in order to try extracting the files via terminal. that did not work because the filenames were probably too long or with the wrong signs...but then it worked with fileroller :)

---

