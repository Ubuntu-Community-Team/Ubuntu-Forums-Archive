---
title: "Samba create mask strangeness"
date: 2006-02-08
forum: Networking &amp; Wireless
---

### Post by el3ktro on 2006-02-08
Hi,
I'm setting up a Samba server with per-user access. In my smb.conf, I've set this:

create mode = 0660
directory mode = 0770

so all newly created files on the server should have the permissions -rw-rw----, but instead, they have -rwxrw----, which is 760 and not 660.

In /etc/profile on the server I've set the umask to 022. Whats wrong here? Do I have to change "create mask" or is the umask wrong (which is the Ubuntu default)?

Tom

---

