---
title: "smb://ip_address trouble"
date: 2009-01-31
forum: Networking &amp; Wireless
---

### Post by rolodoom on 2009-01-31
Since a few days ago I noticed that I can't access my desktop computer  from my laptop computer using Places>Network but I can access it using smb://desktop_computer_ip_address

I've been searching and haven't found an answer.

Any suggestion?

---

### Post by Iowan on 2009-01-31
See if [this]("http://www.sigmundvoid.com/2007/08/netbios-names-and-ubuntu/") one helps.

---

### Post by rolodoom on 2009-03-04
I followed the link.

Now I can:

1. ping to windows_server_name
2. smb://windows_server_name
3. smb://ip_address
4. [http://ip_address](http://ip_address)

but still can't:

1. [http://windows_server_name]("http://windows_name_server")

any clue??

---

### Post by rolodoom on 2009-03-19
Pc is on DHCP.

---

### Post by Iowan on 2009-03-20
I'm away from my favorite Ubuntu machine - with all my favorite bookmarks.  There is a thread around here somewhere explaining how to let Samba see and be seen on Windows network.  *Seems* like it involves nsswitch.conf and Winbind...

---

