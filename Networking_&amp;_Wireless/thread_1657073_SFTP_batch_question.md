---
title: "SFTP batch question"
date: 2010-12-31
forum: Networking &amp; Wireless
---

### Post by SRTS on 2010-12-31
Hi, I'm using SFTP -b to download log files in batch mode.

Problem is: I only want new log files transferred, so it won't transfer all the old log files that it had already transferred previously.

So, how do I tell SFTP to skip existing files instead of overwriting them all?

thanks!

---

### Post by SRTS on 2011-01-01
hello? ^^

---

### Post by IngmarBrouns on 2011-01-01
Hey, I would use rsync  for this (man rsync). With rsync it is very easy to synchronize remote files/dirs. 
It sends only the differences between files. So even if you already have the file, but more entries were added to it, 
then only these entries are copied...

---

### Post by SRTS on 2011-01-01
I'll give it a try. appearently SFTP is still in beta, doesnt have an option for skipping existing files yet.
thanks

---

