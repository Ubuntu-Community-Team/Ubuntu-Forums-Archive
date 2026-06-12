---
title: "Samba - I can't remove old, invalid shares"
date: 2009-10-30
forum: Networking &amp; Wireless
---

### Post by ethridgela on 2009-10-30
I recently reorganized one of the drives on my server, making some old samba shares invalid.  Now, however, I find that my old shares can't be deleted.  I've spent several hours Googling for answers and reading forum threads to no avail, so I'm hoping someone here can help.

In nautilus, when I bring up a directory of smb://myserver/share/ I get some old share names that are no longer valid.

I've read that they should be listed in /etc/samba/smb.conf, but they're not there.  I've checked both the client and the server.

I've also read that I should be able to delete them using:
net usershare delete my_share_name
I've tried that on the client and the server, and I get the same error:
"unable to remove usershare /var/lib/samba/usershares/my_share_name. Error was No such file or directory"

I checked, and the directory /var/lib/samba/usershares is empty on the client and the server.

I'm currently doing a text search for the name of one of the shares in every file in the client filesystem, but that's going to take forever.

What did I miss?  Where are these shares defined?  How do I make these old, invalid shares go away?

---

### Post by ethridgela on 2009-10-31
It's odd that this isn't documented anywhere that I've seen.  After a bit of *thinking* (which sometimes helps, as opposed to blindly Googling) I decided to search for folders named "samba".

```
sudo find / -iname samba
```This revealed that there was a /srv/samba folder on the server, which contained the usershares I had been unable to locate.  I also found that I had left folders in my /media folder, which were formerly used for mounting the old shares. :redface:

Meanwhile, I've purged the samba installation from the server (having found several smb.conf files, and other offenses against humanity) and will start over.

---

### Post by ethridgela on 2009-10-31
I would have marked this thread as [solved] but I don't see the "Edit Thread" menu, even though I'm the original poster.

---

### Post by ST3ALTHPSYCH0 on 2009-10-31
It's under the thread tools menu above the first post on the right hand side... it took me forever to find it too.

---

### Post by ethridgela on 2009-11-01
Thanks!

---

