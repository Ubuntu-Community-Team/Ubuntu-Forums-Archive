---
title: "Why windows see samba duplicate folders"
date: 2010-12-06
forum: Networking &amp; Wireless
---

### Post by legendbb on 2010-12-06
configured /etc/samba/smb.conf
[INDENT]=== Share Definitions ===
[home]
[INDENT]comment = Home Directories
browseable = yes
writeable = yes

[/INDENT]valid user = %S

[/INDENT]Windows connection to the server by \\server_ip
if no pass entered,  network will see one folder "homes", entered pass it will see two identical folders: "homes" & "user_name"

how to make it only one folder visible?

If I commented out [homes], no folder is visible.

thanks,

---

