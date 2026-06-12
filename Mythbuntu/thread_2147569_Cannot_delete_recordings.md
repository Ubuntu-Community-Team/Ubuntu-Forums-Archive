---
title: "Cannot delete recordings"
date: 2013-05-22
forum: Mythbuntu
---

### Post by drewdin on 2013-05-22
I am running .24 fixes 11.10, everything has been working fine until a few days ago when i tried to delete a few recordings. I go into manage recordings, select the recording and him M. I navigate down to delete and hit yes. it disappears from the screen, good right? I noticed that the GB counted at the bottom does not increase showing me that I got the space back, then i move on and delete a few other recordings. As i hit the fourth one to be deleted, I notice that the first one comes back, then the second and so on. 

Has anyone else had this same error? I tried updates and restarting the machine but nothing worked. Thanks

---

### Post by Bucky Ball on 2013-05-22
Can't answer your question but you are running 11.10? If so it has reached end-of-life and you should upgrade to a supported release. There will be no updates, including security updates, for 11.10 and that is a bad thing and risky. 

Good luck.

---

### Post by drewdin on 2013-05-22
I agree, i just got the notice a few days ago that it is an unsupported release. I guess I'll have to backup the DB and upgrade, re-import the db and see what happens.

---

### Post by Bucky Ball on 2013-05-22
Probably a good idea. Might be a waste of time trying to fix this if an upgrade changes things anyhow (or fixes them for you). ;)

---

### Post by tgm4883 on 2013-05-22
We can't possibly help without seeing the log file from /var/log/mythtv/mythbackend.log

---

### Post by larsolav on 2013-05-22
Looks like Myththv can't delete the files. Check the backend log. It may say that the mythtv user does not have permission to delete the files. I had the same problem where for some reason some of the first recordings on my new upgraded setup in December did not have mythtv as the owner so mythtv could not delete them. Once I changed the ownership to mythtv they deleted ok from the mythmenu.

---

### Post by drewdin on 2013-05-22
> **larsolav said:**
> Looks like Myththv can't delete the files. Check the backend log. It may say that the mythtv user does not have permission to delete the files. I had the same problem where for some reason some of the first recordings on my new upgraded setup in December did not have mythtv as the owner so mythtv could not delete them. Once I changed the ownership to mythtv they deleted ok from the mythmenu.

Ill check this when i get home later along with the backend logs and post them. Thanks

---

### Post by drewdin on 2013-05-22
Recently I added a 2 gig drive, moved all of my recordings over to it. It was a permissions setting, set everything to mythtv and now I'm good. Thanks guys

---

### Post by Bucky Ball on 2013-05-23
Excellent news. Please mark thread as Solved by following the link in my signature.

---

