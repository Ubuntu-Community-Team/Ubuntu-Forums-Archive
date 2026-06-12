---
title: "users and groups"
date: 2007-02-10
forum: Multimedia &amp; Video
---

### Post by rbtprkr on 2007-02-10
Hi, I ham trying to install mythtv on Ubuntu edgy. I would like to reset the password for the user mythtv  but the user isn't listed in the users section and I don't see a way to show all of the users and groups like the check box that Dapper has

---

### Post by kidders on 2007-02-10
Hi there,

If it were me, I would first do **grep mythtv /etc/passwd** to check that the user exists, and then reset the password with **sudo passwd mythtv**.

---

