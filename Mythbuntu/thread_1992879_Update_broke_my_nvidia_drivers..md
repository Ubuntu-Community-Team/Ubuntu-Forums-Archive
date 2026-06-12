---
title: "Update broke my nvidia drivers."
date: 2012-06-01
forum: Mythbuntu
---

### Post by rramesh on 2012-06-01
Hi,

  I have 10.04 (Ubuntu 10.04.4 LTS) and have not updated for a while. Today I bit the bullet and updated. Update completed without any error message except that I was told that I should reboot for the update to complete. So I did. However after the update, my nvidia (binary) driver was missing. A bit of investigation made me conclude that nvidia-current did not install properly. I did a reinstall and it kept telling me that the module was not built because no kernel source for my version
(my uname says: Linux xxx 2.6.32-41-generic-pae #89-Ubuntu SMP Fri Apr 27 23:59:24 UTC 2012 i686 GNU/Linux) I tried installing linux-source-2.6.32 and that does not work. I do not know what else is needed.

What is the general recommendation about updates? Do it or not do it? If former then frequently or infrequently? Is it not a good idea to stay with an LTS release?

Ramesh

---

### Post by rramesh on 2012-06-01
It fixed itself. None of my attempt to install nvidia-current worked. However
I went into control center and chose 173 driver and then back to current driver
and everything sorted out. I still do not know what happened. But, I nolonger
have the missing driver problem.

Ramesh

---

