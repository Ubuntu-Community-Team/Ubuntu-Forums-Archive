---
title: "how to remove old Samba share folders?"
date: 2009-02-28
forum: Networking &amp; Wireless
---

### Post by DeepLake21 on 2009-02-28
I see old share folders on the client laptop, but I can't locate them on the desktop server PC. i am using SAMBA.

SAMBA.CONF only shows the share folders that I want. i can't locate the older shard folders in this file! (the show up as empty folders in the client) I would appreciate it if some one can help me locate the old share folders so I can remove.

---

### Post by Iowan on 2009-03-01
The info may be in */var/lib/samba/usershares*

---

### Post by DeepLake21 on 2009-03-01
Indeed it is where you indicated. Problem solved and thanks.

---

### Post by bossfn on 2009-03-09
> **Iowan said:**
> The info may be in */var/lib/samba/usershares*


Excellent tip; I've tried looking through the /etc/samba/smb.conf before and nothing was listed in there. Sure enough all my shares were in the exact location you described, and a quick 'rm' got rid of whatever I no longer wanted.

Thanks a ton!

---

### Post by noletolucas on 2010-06-01
cool...

but is it right to hard remove this directory?

shouldnt we use a tool for that and then get samba.conf synch'ed with /var/lib/samba/usershares ?

---

### Post by noletolucas on 2010-06-01
From: [http://samba.org/samba/docs/man/manpages-3/smb.conf.5.html](http://samba.org/samba/docs/man/manpages-3/smb.conf.5.html)

net usershare add sharename path [comment] [acl] [guest_ok=[y|n]]
To create or modify (overwrite) a user defined share.

[B]net usershare delete sharename
To delete a user defined share.
[/B]
net usershare list wildcard-sharename
To list user defined shares.

net usershare info wildcard-sharename
To print information about user defined shares.

---

### Post by Iowan on 2010-06-01
Thread is over  year old - you may start a fresh one if you wish...
PM me (or use "Report abuse" button) if you wish posts moved.

---

