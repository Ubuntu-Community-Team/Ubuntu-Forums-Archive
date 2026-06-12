---
title: "files download?????"
date: 2011-03-03
forum: Networking &amp; Wireless
---

### Post by vivek.pandey on 2011-03-03
hi everyone
   today itself i joined a shell account given to me by cjb.net.. i am able to ssh shell.cjb.net from my putty... but how can i download files or get help from the this server... i mean as far as i know these shell accounts give you files and help you know more about shell..i have bash shell

anybody with a solution ?
thanx in advance

---

### Post by aeiah on 2011-03-03
from their page:
> How do I download or upload files?
You may transfer files using SCP, SFTP, or the server's command line utilities.

incidentally, cjb offers freeBSD shell accounts, not ubuntu (or even linux) ones. not that this should be much of an issue since they're all very similar, especially in userland.

---

### Post by aeiah on 2011-03-03
you can access the files with an ftp browser, winscp (on windows), mount the ssh location in nautilus, or use the command line scp (or pscp with putty) to copy files to and from your shell account's disk space.

---

