---
title: "Network Drive Mount"
date: 2006-04-28
forum: Networking &amp; Wireless
---

### Post by utab on 2006-04-28
Hi all,

I am having problems with a network pool where we share documents with other colleagues. The problem is that I have to mount this drive on every start-up. I am looking for something like automount, I have learned there is something like that, but dont know how to apply.

SO any help is greatly appreciated.

Regards.

---

### Post by Koybe on 2006-04-28
You should use your /etc/fstab to automount parition.

Have look here : [https://wiki.ubuntu.com/AutomaticallyMountPartitions?highlight=%28mount%29](https://wiki.ubuntu.com/AutomaticallyMountPartitions?highlight=%28mount%29)

It's the same for network share, but it depends if you're using nfs or samba.

GL.

---

