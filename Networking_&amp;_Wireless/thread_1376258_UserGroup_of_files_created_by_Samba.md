---
title: "User/Group of files created by Samba"
date: 2010-01-09
forum: Networking &amp; Wireless
---

### Post by carlsiu on 2010-01-09
I set samba to share my public directory /home/myname/public to everyone without password using security = share option.

For public directory section:
[public]
path = /home/myname/public
read only = no
guest ok = yes
force user = myname
force group = myname

People can now read and write to my public directory. The only problem is that those files created are all owned by nobody:root. How can I force them to be owned by myname:myname?

Thanks!

---

