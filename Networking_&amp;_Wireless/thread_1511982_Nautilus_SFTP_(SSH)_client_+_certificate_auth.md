---
title: "Nautilus SFTP (SSH) client + certificate auth?"
date: 2010-06-17
forum: Networking &amp; Wireless
---

### Post by pakjebakmeel on 2010-06-17
Hi all,

Anyone knows whether its possible to use the built-in Nautilus SFTP client (places --> connect to server --> SSH) in 10.04 in conjunction with certificate authentication?

I've obviously got it working using password auth but would really like to use certificates.


Thanks.

---

### Post by boingen on 2010-12-21
6 months later... In case someone finds this. A way to use nautilus with certificate authentication is to use the command:

ssh-add <path to key file>

before opening nautilus.  The above command adds the key to the ssh-agent and ssh will use it to authenticate and not ask for a password.

---

### Post by netkaiser on 2011-11-23
Found it, worked.

Thanks!

---

