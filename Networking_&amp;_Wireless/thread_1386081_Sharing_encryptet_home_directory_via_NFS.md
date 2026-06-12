---
title: "Sharing encryptet home directory via NFS"
date: 2010-01-20
forum: Networking &amp; Wireless
---

### Post by KING HENRY VIII on 2010-01-20
Hi Folks!

I have now spent hours of searching the net for a solution, without any success. Therefore I'm posting my problem here now:

I have two Xubuntu machines, both run Karmic and have encrypted home directories (set up during the Xubuntu installation, so they're encrypted with ecryptfs). Now I want to share the home directories via NFS for easier file exchange. So I set up the /etc/exports, running ```
sudo exportfs -ra
``` gives me following error: ```
exportfs: Warning: /home/blabla/ does not support NFS export.
```

I created a directory /test/ and everything worked fine. So the problem is the encryption.

Is there any solution or nice workaround for this problem?

Thanks a lot!
Heinrich

---

### Post by KING HENRY VIII on 2010-01-25
I can share it with Samba. Not my favorite solution, but at least it works...

---

### Post by bulislaw on 2010-02-18
try sshfs -> works for my full disk encryption

---

