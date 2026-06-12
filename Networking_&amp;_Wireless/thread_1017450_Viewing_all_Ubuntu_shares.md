---
title: "Viewing all Ubuntu shares"
date: 2008-12-21
forum: Networking &amp; Wireless
---

### Post by reev3r on 2008-12-21
I am somewhat of a Linux n00b trying to ascertain whether or not it is possible to view all the currently active shares in Ubuntu 8.04. I know that I have several shares currently active, but when trying to view them in shares-admin I see no shares. Any help would be greatly appreciated. I am somewhat proficient with Ubuntu so you should not have to dumb it down completely, but maybe a little.

Thanks again,
~reev3r

---

### Post by superprash2003 on 2008-12-21
in your terminal type smbtree .. or go to places->computer and under location type smb://127.0.0.1

---

### Post by reev3r on 2008-12-21
I do appreciate your assistance with that, it worked perfectly. I am also curious what I can to to delete all shares and essentially start over as I am have some permission issues. Again, any help would be greatly appreciated.


~reev3r

---

### Post by Iowan on 2008-12-21
Shares should be defined under either */etc/samba/smb.conf* or */var/lib/samba/usershares*.

---

