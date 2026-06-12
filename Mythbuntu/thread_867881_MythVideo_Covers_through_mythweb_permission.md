---
title: "MythVideo Covers through mythweb: permission"
date: 2008-07-23
forum: Mythbuntu
---

### Post by Dumdideldum on 2008-07-23
I am facing problems whenever I upload a cover through mythweb for my videos (mythvideo). The Cover gets shown in mythweb, but it isn't shown in mythtv itself, until I chmod the cover file from 700 (www-data) to 777, so that the user mythv can read it too.

Is there any possibility to let www-data (which runs apache) write the cover file to 777 or 755 (assuming mythtv is in www-data group), so that the user mythtv can read it afterwards without the need of chmod ?

thx a lot

---

### Post by Weidbrewer on 2008-07-26
I'm having the same issue.  Figured that I'd post to bump this up for you.  But yeah, basically my problem is that I can't assign covers and have them stick when done in MythWeb.

---

### Post by Dumdideldum on 2008-09-03
another bump - anyone got an idea ?

---

### Post by SiHa on 2008-09-03
How about a cron job that periodically just does```
chmod 777 /path/to/covers/*
```
??

A bit dirty, but it would probably work...

...wouldn't it?

---

### Post by Dumdideldum on 2008-09-03
yes sure it would, but I look forward to filing a ticket if this problem doesn't just affect me (or one or two other guys) - so, any others who are facing the same problem ?

The file created through mythweb is definitely 600, so even adding the user running frontend to the www-data group doesn't solve this issue.

---

### Post by jackthecoiner on 2009-01-07
Here's another bump as I've run into the same problem.  I'll see if I can find the offending script and make a patch.  In the meantime, if anyone has solved this, please share your solution.

---

### Post by jackthecoiner on 2009-01-07
For those interested I filed a bug here and placed a patch in it which fixes the permissions problem:

[http://svn.mythtv.org/trac/ticket/6086](http://svn.mythtv.org/trac/ticket/6086)
[http://svn.mythtv.org/trac/attachment/ticket/6086/patch.txt](http://svn.mythtv.org/trac/attachment/ticket/6086/patch.txt)

I don't have checkin rights, so it may be a while before the patch is on the trunk, but it's a very simple one line change to:
/var/www/mythweb/modules/video/edit.php

After the line:
move_uploaded_file($_FILES['coverfile']['tmp_name'], $filename);

Add the following:
chmod($filename, 0644); // make cover file readable by other users

---

