---
title: "nfs share will not auto mount with fstab, rc.local or autofs"
date: 2010-12-05
forum: Networking &amp; Wireless
---

### Post by houserparker on 2010-12-05
Hi all,

I have left the Ubuntu forums as a last resort but have now been researching this problem for a week to no avail.

I can mount my nfs share on client manually after login with the following command but cannot mount nfs share via fstab, rc.local or autofs.

manual mount after login

```
sudo mount 192.168.1.1:/home/ben/BensShare /home/ben/NFSShare
```

fstab entry

```
192.168.1.1:home/ben/BensShare /home/ben/NFSShare nfs _netdev,bg,hard,rsize=8192,wsize=8192,defaults 0 0
```

rc.local entry which is the same command i use to mount manually with success.

```
sudo mount 192.168.1.1:/home/ben/BensShare /home/ben/NFSShare
```


Errors I have been receiving in the boot log are as follows which I have also googled.

mount.nfs: Failed to resolve server 192.168.1.1: Name or service not known
mountall: mount /home/ben/NFSShare [933] terminated with status 32

Any help would be much appreciated as without I don't think I'll be able to solve this one.

Thanks,

---

### Post by houserparker on 2010-12-06
does any one want to have a shot?

---

### Post by houserparker on 2010-12-07
Can anyone help?

---

### Post by houserparker on 2010-12-07
I found the problem. A stupid mistake.

It should have been,

```
192.168.1.1:**/**home/ben/BensShare /home/ben/NFSShare nfs _netdev,bg,hard,rsize=8192,wsize=8192,defaults 
```

Leaving out the forward slash accented in **bold** being the mistake I made.

---

