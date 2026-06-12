---
title: "Recording to a separate partion"
date: 2011-02-01
forum: Mythbuntu
---

### Post by tagscott on 2011-02-01
I have a master backend and a remote frontend. I added a new TB drive for my media and want to use my old media partition as a place to store recordings. I have the TB drive mounted as /myth and the old partition mounted at /var/lib/mythtv/recordings . I copied my old recordings from the old recording folder to the partition and mounted it. Now myth does not see the files. New recordings are added to the list but are not found and files dont exist in the folder. Any help is appreciated.

---

### Post by newlinux on 2011-02-01
make sure you storage group points to where you have the recordings (I believe you have them at the default place, so unless you changed it that should be okay). Also make sure the mythtv user has read/write access to the recordings folder.

What do you mean by new recordings are added to the list? Does it actually record them?

---

### Post by klc5555 on 2011-02-01
When you set up your new /var/lib/mythtv/recordings partition, you may have left it under owner "root" and group "root" You'd need to chown and chgrp it to "mythtv", and then set the permissions as something like 775 so that the backend, the frontend and the main user account can all read/write to it properly.

---

### Post by tagscott on 2011-02-02
I tried moving the mount to /media/recordings. I changed the storage group to match, checked the owner:group, which is *my_user*:mythtv and the permissions are drwxrw-rw- which I believe would be 755. All this result in the same issue. The scheduled recordings are listed in the "view recordings" list but files don't exist in the recordings folder

---

### Post by newlinux on 2011-02-02
what do your backend logs contain about the failed recordings? They probably give the reason.

---

### Post by klc5555 on 2011-02-02
> **tagscott said:**
> I tried moving the mount to /media/recordings. I changed the storage group to match, checked the owner:group, which is *my_user*:mythtv and the permissions are drwxrw-rw- which I believe would be 755. All this result in the same issue. The scheduled recordings are listed in the "view recordings" list but files don't exist in the recordings folder

Mythtv's path going anywhere through personal user directory space --here: /media (I would assume), and .../recordings -- is frequently a recipe for odd permissions problems. Which is why the default mythbuntu setup puts everything under /var/lib/mythtv owner:group mythtv It's just a lot easier.

If permissions are set up mostly OK, then livetv should be working too. If they're not, then livetv will just kick you back to the main menu. Otherwise, like newlinux says, you'll need to examine the backend log.

---

### Post by nhtrader on 2011-02-04
tagscott,

Can I ask which paths were changed by you in the BE and FE to make the redirection complete (officially recognized by MythTV)?

---

### Post by tagscott on 2011-02-15
Apparently it didnt like using *my_user* as the owner. I moved the mount back to /var/lib/mythtv/recordings, pointed the storage group to it, and chown to mythtv:mythtv Now everything works like it should.

---

