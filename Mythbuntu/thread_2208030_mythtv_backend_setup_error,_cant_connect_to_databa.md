---
title: "mythtv backend setup error, cant connect to database?"
date: 2014-02-26
forum: Mythbuntu
---

### Post by sdowney717 on 2014-02-26
I just installed mythTV

ran the mythbackend config and says it cant connect to database.
It shows a huge page with various configuration settings.

username mythtv, password mythtv 
localhost port 3306
etc...

So what do you do to make it work?

---

### Post by sdowney717 on 2014-02-26
went ahead and ran frontend, backend keeps coming up with the error, so the database issue has got to be resolved.

---

### Post by sdowney717 on 2014-02-26
[https://help.ubuntu.com/community/MythTV/Install/Troubleshooting#head-75ded5e7682340f0a88f9ed6ec69a68b6a8b4162](https://help.ubuntu.com/community/MythTV/Install/Troubleshooting#head-75ded5e7682340f0a88f9ed6ec69a68b6a8b4162)

following, this I ended up having to uninstall it all.
then reinstall with NO mysql password. 
Now it connects to the backend.

---

### Post by Bobby Infinity on 2014-03-12
[http://askubuntu.com/questions/237362/mysql-access-denied-for-user-root-while-using-lamp](http://askubuntu.com/questions/237362/mysql-access-denied-for-user-root-while-using-lamp)

The above link kept me from having to uninstall and reinstall. After that, I followed the link you posted.

---

