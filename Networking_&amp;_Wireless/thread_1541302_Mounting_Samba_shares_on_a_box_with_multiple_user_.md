---
title: "Mounting Samba shares on a box with multiple user accounts"
date: 2010-07-29
forum: Networking &amp; Wireless
---

### Post by rlwpub on 2010-07-29
I setup samba file sharing to auto mount in fstab. Everything works great except when a computer has more than on user account.

The folders in mnt are owned by root and ownership changes to the first user account no matter what user logs in. So only the first user can edit files in the mounted share.

Anyone got a clue why this is happening? Seems the mount folders should be changing ownership to the user that is logged in.

---

### Post by cj.surrusco on 2010-07-29
Try using the 'noperm' option on the mount. There is a whole HOWTO on the fstab [here]("http://ubuntuforums.org/showthread.php?t=283131").

---

### Post by rlwpub on 2010-07-29
> **cj.surrusco said:**
> Try using the 'noperm' option on the mount. There is a whole HOWTO on the fstab [here]("http://ubuntuforums.org/showthread.php?t=283131").

Thanks. The noperm seems to have solved the problem. I'll get some others that have accounts on the box to see if they can now edit files also.

---

