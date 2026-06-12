---
title: "NFS mounting fails (mount(2): Input/output error, mount system call failed)"
date: 2010-05-06
forum: Networking &amp; Wireless
---

### Post by bjtuna on 2010-05-06
I have been using Ubuntu for several years now. I have always had the following line in /etc/fstab:

```
192.168.0.30:/shares/SimplePool/Storage /home/brian/Storage nfs rw,auto,rsize=8192,wsize=8192,intr,soft,retry=5 0 0
```

That, along with having ```
nfs-common
``` installed, has always worked great for accessing my remote NFS server.  Unfortunately Ubuntu 10.04 (Lucid) isn't cooperating.

If I try to manually mount /home/brian/Storage it will hang. I ran the following equivalent command to debug:

```
sudo mount -v -t nfs -o rw,auto,rsize=8192,wsize=8192,intr,soft,retry=5 192.168.0.30:/shares/SimplePool/Storage /home/brian/Storage
```

And the result was:

```

mount.nfs: timeout set for Thu May  6 10:01:01 2010
mount.nfs: text-based options: 'rsize=8192,wsize=8192,intr,soft,retry=5,addr=192.168.0.30'
mount.nfs: mount(2): Input/output error
mount.nfs: mount system call failed

```


And to answer the questions you are all itching to ask: yes, portmap is installed, and no, there is no firewall.

Any help would be greatly appreciated! Thanks!

---

### Post by bjtuna on 2010-05-08
Nevermind. I rebooted the NFS server and it worked.

---

