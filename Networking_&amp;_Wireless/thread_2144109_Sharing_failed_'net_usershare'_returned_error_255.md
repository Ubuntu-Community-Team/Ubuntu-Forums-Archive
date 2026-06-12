---
title: "Sharing failed: 'net usershare' returned error 255"
date: 2013-05-11
forum: Networking &amp; Wireless
---

### Post by gpsvn on 2013-05-11
When sharing a folder, I got this error message.

'net usershare' returned error 255: net usershare add: cannot convert name "Everyone" to a SID. Memory allocation error.

Searching the forum, I found an old thread and tried to run **sudo /etc/init.d/samba4 restart **from terminal. It did not help. I then run **sudo service samba4 restart**, as suggested by Ubuntu but problem still not solved yet.

Appreciate any guidance.

---

