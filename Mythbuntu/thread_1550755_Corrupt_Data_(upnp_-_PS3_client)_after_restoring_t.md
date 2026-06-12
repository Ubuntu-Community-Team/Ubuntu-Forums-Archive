---
title: "Corrupt Data (upnp - PS3 client) after restoring the database"
date: 2010-08-11
forum: Mythbuntu
---

### Post by A_arthur_N on 2010-08-11
Long time Mythtv user with a new issue.

Reinstalled Ubuntu (and later installed mythbuntu-desktop).  Restored my database via supplied scripts.  

I set up a root MySQL account during installation and afterwards I had to set the mythconverg username as root with the password I chose.

All seemed fine.  I can watch old recordings on my frontend/backend.  There are a couple of problems I have recently discovered:

1.  When I tried to add my laptop as a frontend I can't connect to the backend ("cannot" is all that comes up when I supply the root password and correct IP address)

2.  When using a PS3 as a upnp client I cannot watch anything that was recorded prior to the restoration of the database.

I think that 1 and 2 might be connected and that there might be an issue with using the "root" account which I have never done before (didn't think about it when asked for a password I just put one in)

Any help would be appreciated.

Cheers

Arthur

---

### Post by nickrout on 2010-08-11
you need to give the remote frontend the mythtv mysql passwod, not the root password.

on the machine that works look in /home/user/.mythtv/mysql.txt

where user is the user that runs mythfrontend.

As far as the upnp goes, check permissions, ownership and logs.

---

### Post by A_arthur_N on 2010-08-11
I changed all owners to mythtv (group mythtv) and all permissions to rw (owner, group and all) and still only the new files work on the PS3.  Everything works great on the backend/frontend PC but upnp clients cannot play the restored files.

The laptop issue has been solved.

Arthur

---

### Post by nickrout on 2010-08-12
Time to look at your logs then.

---

