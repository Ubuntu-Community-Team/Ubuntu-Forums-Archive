---
title: "Ubuntu won't share over Samba"
date: 2009-08-26
forum: Networking &amp; Wireless
---

### Post by Superdude_123 on 2009-08-26
I'm working with ubuntu 9.04, and I created a folder located at /, and I've changed the rights to it by doing a chmod 777 to the folder, however, on my windows PC, I can see the ubuntu system, but once I open it I can't write to it. What am I doing wrong? Also, does it make a difference that the windows system is part of an other work group, but through the MS network tree, I find the system that way?

---

### Post by Jose Catre-Vandis on 2009-08-26
Try here

[http://ubuntuforums.org/showthread.php?t=1169149&highlight=samba](http://ubuntuforums.org/showthread.php?t=1169149&highlight=samba)

and /or here

[http://ubuntuforums.org/showthread.php?t=202605&highlight=samba](http://ubuntuforums.org/showthread.php?t=202605&highlight=samba)

but not a great idea to look to share / ! Suggest you reorganise the shares a bit to a lower level or a mount in /media

---

### Post by Superdude_123 on 2009-08-26
Didn't work. How could I check if its my windows system's fault?

---

### Post by Iowan on 2009-08-26
Might need to post your */etc/samba/smb.conf*. Depending on how permissions are set for the share, your user may need to be included in **authorized users=** or **write access=** options or there's the **force user=** option.

---

