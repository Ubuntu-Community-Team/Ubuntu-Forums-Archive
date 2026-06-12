---
title: "Creating x setup with two x servers for two monitors"
date: 2008-08-28
forum: Multimedia Software
---

### Post by RMKrug on 2008-08-28
Hi

I have an ati graphic card on a notebook, and would like to have a dual-screen setup with two x servers with the OpenSource driver. I have this setup at the moment with the proprietary driver, but would [prefer to use the OpenSource driver.

Is this possible? I googled around, but could not find anything useful with the OS driver.

Thanks

Rainer

---

### Post by forger on 2008-08-28
Something like this?
[http://linuxgazette.net/124/smith.html](http://linuxgazette.net/124/smith.html)

edit: also found these:
[http://tech.yahoo.com/blog/null/24753](http://tech.yahoo.com/blog/null/24753)
[http://www2.userful.com/products/downloads/free-2-user](http://www2.userful.com/products/downloads/free-2-user)
[http://gentoo-wiki.com/HOWTO_get_2_users_on_1_pc](http://gentoo-wiki.com/HOWTO_get_2_users_on_1_pc)

---

### Post by RMKrug on 2008-08-28
Actually no - something like the dual-head from ati:

 aticonfig --initial=dual-head --screen-layout=above

produces the setup I am using at the moment.

---

### Post by djRobbieF on 2008-08-28
With an nVidia card, it's so simple just using *nvidia-settings*.  (just thought I'd mention that in case anyone was looking for the answer and using nVidia).

---

