---
title: "Network two Ubuntus"
date: 2010-05-18
forum: Networking &amp; Wireless
---

### Post by Doug11 on 2010-05-18
i have Ubuntu on my desktop and laptop. Most of my backup files are on my desktop. How do I go about creating a small home network to share between the two?

---

### Post by mikewhatever on 2010-05-18
Right click a folder you want to share, select 'Sharing Options'...

---

### Post by fix_ on 2010-05-18
> **Doug11 said:**
> How do I go about creating a small home network to share between the two?

In addition to recommended, I can propose you to try sftp protocol. Install openssh-server package on the desktop. Then navigate to you Desktop PC from your desktop environment in the way sftp://user@192.168.1.10 (your user and ip here).

---

### Post by Doug11 on 2010-05-18
> **fix_ said:**
> In addition to recommended, I can propose you to try sftp protocol. Install openssh-server package on the desktop. Then navigate to you Desktop PC from your desktop environment in the way sftp://user@192.168.1.10 (your user and ip here).
OK thanks,,I will give this a try and see how it goes.

---

### Post by Doug11 on 2010-05-18
ok,,i got it to work somewhat by using the remote desktop and then typing in vnc://(your ip)  I haven't tried any file transfers yet though.

---

### Post by Doug11 on 2010-05-19
This only works as a remote login. I'm not quite sure how to go about the openssh,,,though i do see it install in synaptic.

---

### Post by mikewhatever on 2010-05-19
Yes, search for it in Synaptic or use this command:

sudo apt-get install openssh-server

PS: I really like it, thanks fix_.

---

