---
title: "Large .old Samba Log Files"
date: 2010-03-27
forum: Networking &amp; Wireless
---

### Post by KCLU on 2010-03-27
Hi, I'm new to the forums so hopefully this is the correct category.
 
I have a problem with Samba creating excessively large log files which can crash my server.
 
I have a limit of 1000k on log files which seems to work, but once this limit is reached on the log.%m file the contents are transferred to a log.%m.old file which is not limited.
 
I have one Windows XP PC which has been have problems which I am working on fixing but this has many times generated a log.%m.old file which has reached 389G and filled the server.
 
How can I either prevent these .old files being created or limit thier size also?
 
Many thanks in advance.
 
Richard

---

### Post by Barriehie on 2010-03-28
**find** can search based on size and then you can do whatever with them.
As root:
```

find /var/log/ -size +1000k -print
```Just print them out.


OR

```

find /var/log/ -size +1000k -exec rm {} \;
```to delete them.

---

### Post by KCLU on 2010-04-05
Thanks for this and apologies for the delay in replying.
 
This is useful information on how to clear the files, but is there a way to prevent the files being created or getting that large through Samba in the first place?

---

### Post by capscrew on 2010-04-05
> **KCLU said:**
> Thanks for this and apologies for the delay in replying.
 
This is useful information on how to clear the files, but is there a way to prevent the files being created or getting that large through Samba in the first place?

I would think that curing the problem that is causing the logs to grow would be more appropriate that modifying the the alert system.  I have a small Samba server that I use for testing and have never needed to delete a log file.

You might try setting up logrotate This should be able to overwrite the log you determine to be the least needed.  See [**_here _**]("http://www.linuxconfig.org/logrotate") and [**_here_**]("http://linuxers.org/howto/howto-use-logrotate-manage-log-files").

---

### Post by capscrew on 2010-04-05
double post.

---

