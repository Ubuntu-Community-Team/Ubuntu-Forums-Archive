---
title: "Copying files to an SMB share"
date: 2012-05-18
forum: Networking &amp; Wireless
---

### Post by theccman on 2012-05-18
Hi all!

I can access an SMB folder in LAN through "smbclient //server/share". How can I copy some files to this folder? Do I have to mount this folder or isn't it necessary?

---

### Post by sikander3786 on 2012-05-18
If the share is writable, you don't need to do anything else. A simple copy/paste is all that is needed.

But if the share is write-protected, you need to ask the Admin to grant you the privileges.

---

### Post by theccman on 2012-05-18
> **sikander3786 said:**
> A simple copy/paste is all that is needed.
OK. How can I do it via command line? I'm seeking for something like:

smbclient //server/share put ./*txt

---

### Post by sikander3786 on 2012-05-18
Take a look here if it helps:

[http://www.odi.ch/weblog/posting.php?posting=343](http://www.odi.ch/weblog/posting.php?posting=343)

---

### Post by theccman on 2012-05-18
> **sikander3786 said:**
> Take a look here if it helps:

[http://www.odi.ch/weblog/posting.php?posting=343](http://www.odi.ch/weblog/posting.php?posting=343)
Thank you very much.

---

