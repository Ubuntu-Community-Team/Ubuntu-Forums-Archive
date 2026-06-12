---
title: "which server should i use??"
date: 2010-06-26
forum: Networking &amp; Wireless
---

### Post by TheOne...more on 2010-06-26
hi, i've started this thread earlier [http://ubuntuforums.org/showthread.php?t=1516782&highlight=copy+local+wget](http://ubuntuforums.org/showthread.php?t=1516782&highlight=copy+local+wget), and the reply i recieved sujested that i needed a server installed on my gutsy box.

what i need is something very easy and as simple as possible to do the task.

so which server should i use?

thanx.

---

### Post by jonobr on 2010-06-26
Have you looked at [Rsync]("http://www.cyberciti.biz/tips/linux-use-rsync-transfer-mirror-files-directories.html") ?
This will allow an rsync client to compare files from the client to the server and copy the difference in the two directories,
You could automate the client to do the copy every day,
I cant recall if rsync is installed by default but it should be easy to install

---

### Post by Iowan on 2010-06-26
I haven't tried since I upgraded to Hardy, but...
Since [Gutsy]("http://ubuntuguide.org/wiki/Ubuntu:Gutsy") is no longer supported, it might be hard to find an FTP server in the repos.

---

