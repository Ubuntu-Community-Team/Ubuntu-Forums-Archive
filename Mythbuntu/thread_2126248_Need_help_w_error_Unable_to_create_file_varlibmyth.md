---
title: "Need help w/ error: Unable to create file: /var/lib/mythtv/videos//.test"
date: 2013-03-16
forum: Mythbuntu
---

### Post by donb21 on 2013-03-16
I get this error when I try to exit myth-tv setup, but this file does not exist.  The //.test looks suspicious, maybe a database error?  Any idea what to do about it?

---

### Post by klc5555 on 2013-03-16
This is usually an owner/group/permissions problem on the selected directory. The user "mythtv" doesn't have sufficient permissions to write to the directory, which frequently happens if a new storage drive or similar has just been mounted to /var/lib/mythtv/videos Check that the .../videos directory is owner/group  mythtv:mythtv  (as opposed to, say, root:root, or [you]:users)   The permissions should be set something along the lines of 775. 

And your main user should be added to the mythtv group at some point, if the setup didn't take care of this already.

---

### Post by donb21 on 2013-03-16
That did it.  /var/lib/mythtv/video was setup as mythtv:nogroup.  I changed it to mythtv:mythtv and added my user to the mythtv group.  Error's gone, but I wonder why user "mythtv" wasn't good enough.  Thanks for the help.
 
For reference, this is the command I used to add the user:
don@zedo:~$ sudo usermod -a -G mythtv don

---

