---
title: "Permission problem between pam_mount and public_html"
date: 2011-12-16
forum: Networking &amp; Wireless
---

### Post by enboig on 2011-12-16
I have followed [http://lists.samba.org/archive/samba/2011-March/161394.html](http://lists.samba.org/archive/samba/2011-March/161394.html) to join my computer to a samba server. I changed the mount point from "domain/user" to "user" in order to use apache userdir module, so "localhost/~user" is usable to development.

My problem is Apache complains "You don't have permission to access /~user/index.html on this server."

Any hint? the file is 666 and public_html 755

Thanks.

---

