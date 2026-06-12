---
title: "need help with samba in 6.06"
date: 2006-05-17
forum: Networking &amp; Wireless
---

### Post by DSK on 2006-05-17
I get this error when trying to remove samba with synaptic.

E: samba: subprocess pre-removal script returned error exit status 102

I am running version 6.06 and have the version of samba installed for 5.10 but it will not let me remove it or upgrade it.???????

I am also a fairly new linux/ubuntu user.

---

### Post by DSK on 2006-05-17
Never mind.  I found a solutions in another thread.

This fixed it:
sudo rm /etc/rc2.d/K09samba


***Delete this thread***

---

### Post by chudder on 2006-12-06
Thank you, this helped me, I was looking for a way to do it in the command line and I couldn't find it until now and now the error is gone at least for now.

---

