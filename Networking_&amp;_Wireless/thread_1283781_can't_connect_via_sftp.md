---
title: "can't connect via sftp"
date: 2009-10-05
forum: Networking &amp; Wireless
---

### Post by guitar_man on 2009-10-05
Im trying to connect on my remote pc via sftp,but I cant connect on port 22 using nauiltus.
I just type address on nautilus,it just display "Could not display "sftp://jomel@192.168.0.102/".":confused:

---

### Post by guitar_man on 2009-10-06
anyone????

---

### Post by bogdan.veringioiu on 2009-10-06
Hi.

Were you able to connect before?
Try to test these steps:
-ping the machine;
-ssh into the machine;
What are the results?
Bogdan

---

### Post by guitar_man on 2009-10-06
I was able to connect before I reinstall OS on the host...I'm using nautilus to browse the files but there I cant connect..but not on the terminal...
I can connect using the terminal only,using sftp ang ssh.

---

### Post by bogdan.veringioiu on 2009-10-06
Can you try instead of sftp://jomel@192.168.0.102/, to use:
ssh://jomel@192.168.0.102/ in nautilus??
Bogdan

---

### Post by guitar_man on 2009-10-06
It did connect,,,thanks...but when I restart my computer the bookmark is gone on nautilus..but atleast it connect...thnaks..

---

