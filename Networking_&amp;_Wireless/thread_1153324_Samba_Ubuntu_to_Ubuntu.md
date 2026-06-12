---
title: "Samba: Ubuntu to Ubuntu"
date: 2009-05-08
forum: Networking &amp; Wireless
---

### Post by rick71 on 2009-05-08
I have a Samba Server (hardy) serving a mixed XP/Linux lab. The Windows machines can the see server, connect tp it and move files fine. My Ubuntu machines (hardy) can see the server. They can see the shares (Homes, Shared) but the cannot connect to them.

[homes]
   comment = Home Directories
   browseable = yes
   read only = no 
   valid users = %S

[Shared]
	comment = Shared Directory
	path = /shared
        writeable = yes
	browseable = yes

How can I have users connect to their home directories on the server, and to the shared directory?

Any and all help appreciated.

---

