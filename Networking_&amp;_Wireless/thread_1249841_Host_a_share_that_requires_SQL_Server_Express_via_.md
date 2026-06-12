---
title: "Host a share that requires SQL Server Express via Samba"
date: 2009-08-25
forum: Networking &amp; Wireless
---

### Post by ffoeg on 2009-08-25
Hello. I have had some experience deploying ubuntu desktops as samba servers. I would like to host a database that requires SQL Server Express via a Samba share. But I can't find any definate info on the equivalent of SQL Server Express for Ubuntu. Is there anyone out there who has tried this? Thanks in advance.

---

### Post by dmizer on 2009-08-25
Not sure exactly what you're trying to do, but I hope I can suggest a suitable alternative that will work with Windows clients.

1) Install a LAMP server
```
sudo tasksel
```
Use the arrow keys and the spacebar to select LAMP server from the list and hit <tab> and <enter> to click "ok"

2) Install phpmyadmin
```
sudo aptitude install phpmyadmin
```
3) Configure mysql and add user accounts by browsing to [noparse]http://localhost/phpmyadmin[/noparse]

Not quite the same as SQL Server Express but very similar, and fairly easy to use. Your Windows clients can access the interface by browsing to [noparse]http://ubuntu-server-ip-address/phpmyadmin[/noparse]

---

### Post by ffoeg on 2009-08-26
Hi Mmizer. Thank you for that info. I'll give it a shot when the software that accesses the share becomes available to me. Thank you.

---

