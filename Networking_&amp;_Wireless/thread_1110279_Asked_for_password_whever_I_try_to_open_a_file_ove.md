---
title: "Asked for password whever I try to open a file over SFTP"
date: 2009-03-29
forum: Networking &amp; Wireless
---

### Post by jamieh on 2009-03-29
I'm connected to a server via SFTP, but whenever I try to open a file, it asks me for a password ("Enter the username and password for 192.168.0.106 here"). This box is shown AFTER the OpenOffice splash screen.

There is no text box after the "Username" label, and trying possible passwords doesn't seem to work. I tried chmodding everything to 777 but no dice.

How can I make it so no password is prompted?

Thanks

EDIT: If I drag the file to the desktop, it opens fine.

---

### Post by jamieh on 2009-03-30
Managed to fix it by changing "username" to "username:password".
Use thread for reference.

---

