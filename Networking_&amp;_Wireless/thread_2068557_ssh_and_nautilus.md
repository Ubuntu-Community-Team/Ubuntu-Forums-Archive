---
title: "ssh and nautilus"
date: 2012-10-09
forum: Networking &amp; Wireless
---

### Post by tommpogg on 2012-10-09
Hi,

I am connecting to a remote PC using SSH and I woul like to open nautilus on the remote PC and copy some files to the local one. Both the local PC and the remote one run Ubuntu 10.10.
In order to perform this action, I run the following commands
```

(local)
ssh -X user-name@remoteIP

(remote)
nautilus .

```
Once the nautilus window is open, I just try tocopy and paste the file I'm interested in.
But at this point , the system reports an error stating the the file doesn't exist.

What am I doing wrong? Perhaps I miss some option when I connect with SSH.

Thank you

PD: I already know that I can connect to the remote PC by clicking on Places -> Connect to Server. Actually, this way I can copy whatever I like, but still I'm interested in the other way.

---

### Post by JRV on 2012-10-09
try this:
```

nautilus sftp://USER@HOSTNAME/home/USER

```

---

### Post by tommpogg on 2012-10-10
Thank you, it works.

Anyway, isn't there a way to open nautilus directly from the remote computer and then copy from there?

---

