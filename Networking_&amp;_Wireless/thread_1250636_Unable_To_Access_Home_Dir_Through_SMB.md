---
title: "Unable To Access Home Dir Through SMB"
date: 2009-08-26
forum: Networking &amp; Wireless
---

### Post by nshiell on 2009-08-26
I wasn't able to access my home dir through Samba on any clients following a system hang. 

After reboot I found after a lot of searching that the perms on my home dir had been changed? (System crash I guess)

Anyways doing: - ```
sudo chmod 755 MyHomeDirPath
``` seems to have fixed it.

I am frustrated that the dir perm changed and that Samba's GUI didn't tell me (even after I recreatted the share using the GUI tool), but alls well that ends well I guess.

REMEMBER, if something goes wrong with a UNIX 99% of times it will be rights! (I think this will have to be my signature).

---

