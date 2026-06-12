---
title: "rm: cannot remove `/home/mythtv/.mythtv/mysql.txt': Permission denied"
date: 2008-09-28
forum: Mythbuntu
---

### Post by Buschbarber on 2008-09-28
volkswagner has asked me to post this thread as we have been beating our heads trying to resolve a problem configuring mythtv on my Ultimate 1.9 machine.

I was able to manually delete the file from home/mythtv/.mythtv/mysql.txt, but when I tried to do it using

sudo rm ~/.mythtv -rf && rm /home/mythtv/.mythtv -rf

I get Permission Denied

---

### Post by prshah on 2008-09-28
> **Buschbarber said:**
> 
I was able to manually delete the file from home/mythtv/.mythtv/mysql.txt, but when I tried to do it using
sudo rm ~/.mythtv -rf && rm /home/mythtv/.mythtv -rf


The 'sudo' applies only to the first command; the second command needs sudo as well, if the user giving the command is not "mythtv" (and it doesn't seem to be).

---

