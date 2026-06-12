---
title: "Apache reading a network folder?"
date: 2011-06-24
forum: Networking &amp; Wireless
---

### Post by VcDeveloper on 2011-06-24
How do I properly have apache read a network folder?  I'm running Drupal and I want my http documents on my Windows 7 drive.  And, I would like to do this for MySQL, have all the databases there to.  Want to use Windows 7 as a file server.

Thanks!...

---

### Post by SeijiSensei on 2011-06-25
Unix Apache expects to find filesystems with Unix (actually "POSIX") attributes like permission bits, etc., that NTFS doesn't provide.  You'd be better off running the Windows versions of Apache and MySQL, or moving everything to Linux and sharing the Apache folders back to the Windows machines with Samba.  I use the latter approach in Windows-based organizations so they can save files to the website without needing to know anything about Linux.

I can't really see much rationale for running MySQL on Windows.  Run the databases on Linux and connect to them from Windows using the [MySQL ODBC connector]("http://dev.mysql.com/downloads/connector/odbc/").  I'll sometimes run Microsoft Access to manage remote databases running on Linux hosts via ODBC.

---

### Post by VcDeveloper on 2011-06-26
Good idea!  Thanks for your help!  I'll keep everyone on the Linux and just install a second drive or build two additional Ubuntu servers, 1) as a file server, and 2) MySQL database server.

---

