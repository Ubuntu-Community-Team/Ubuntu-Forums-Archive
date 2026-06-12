---
title: "gFTP  Could not download from local filesystem"
date: 2009-11-15
forum: Networking &amp; Wireless
---

### Post by lingenfr on 2009-11-15
Each time I try to transfer a folder/files, it tells me:

 Could not download /home/me/Desktop/folder/folder or files from local filesystem.

Is this a note problem? Is there a fix? I also tried FileZilla and it is having similar problems. It copies about 1-2/3 of the files but then says it can't open the rest. Thinking it might be choking on deeply nested folders, I moved the source folder to / and still no joy. I assume this is a file system problem of some type either with the application or other.

---

### Post by lingenfr on 2009-11-17
What a complete mess has been made of FTP and related apps. It is unfortunate that no help is forthcoming.

---

### Post by moboticdes on 2011-12-23
Sorry noone answered you before, anyway it must be a problem with permissions.
Set chmod 777 all files and check the owner and the group are the same of the user you are using gftp with.

---

