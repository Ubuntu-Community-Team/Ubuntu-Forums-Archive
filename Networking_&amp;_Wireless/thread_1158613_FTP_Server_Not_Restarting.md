---
title: "FTP Server Not Restarting"
date: 2009-05-13
forum: Networking &amp; Wireless
---

### Post by BlackRat90 on 2009-05-13
i just reasonly installed Pure ftpd on my machine and it was working just fine. but today I went in to change the config and now when I go to restart the server i get this error.

  root@nate-laptop:/etc/pure-ftpd/conf# sudo /etc/init.d/pure-ftpd restart
  Restarting ftp server: /usr/sbin/pure-ftpd-wrapper: Invalid configuration file /etc/pure-ftpd/conf    /MaxClientsNumber~: No corresponding directive

I unforcantly do not understand this at all. It is something wrong with the file I edited, but when i changed back even it still doesnt work.
Anyone have a guess as to the problem??

---

### Post by BlackRat90 on 2009-05-13
found the problem!!
i noticed the file it was having a problem with has a ~ at the end of it. i just deleted the file and it restarted fine!! but now im having connecting issues, which probably has to do with me setting up the user accounts..

---

