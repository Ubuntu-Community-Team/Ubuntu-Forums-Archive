---
title: "A question about SAMBA"
date: 2009-01-15
forum: Networking &amp; Wireless
---

### Post by amit.la on 2009-01-15
Hey all

I've got a question about samba.

I'm using Ubuntu 8.10 on my desktop, and i have an XP notebook. I've installed samba, and the only thing that made my shares on Ubuntu visible, and browsable from XP was adding a section to the smb.conf file
e.g.

[TheNameOfTheShare]
path = /home/myUserName/MyDownloads/SomeFolder
comment = No comment
read only = no
available = yes
browseable = yes
writable = no
guest ok = yes
public = yes
printable = no
share modes = no
locking = no



The question is: Isn't there an easier way of doing that? (just right clicking on the folder, and setting the sharing properties didn't do the trick)

---

