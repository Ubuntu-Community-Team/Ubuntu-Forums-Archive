---
title: "Could not open log '/var/log/apache2/access.log'"
date: 2011-11-09
forum: Networking &amp; Wireless
---

### Post by beradero on 2011-11-09
Hello!
I'm trying to make a cgi script that reads apache's access.log and then writes a report.

The file is world readable:
> -rw-r--r-- 1 root adm 4507 2011-11-09 20:22 /var/log/apache2/access.log


But I keep getting this error message at error.log:
> Could not open log '/var/log/apache2/access.log': Permission denied


When I move access.log to my home dir, the cgi script works fine.

:confused:

---

### Post by beradero on 2011-11-10
No one knows what the problem is?

---

### Post by BillyBoa on 2011-11-10
I tried to access to the .log with sudo nautilus and I don't have problem.

---

