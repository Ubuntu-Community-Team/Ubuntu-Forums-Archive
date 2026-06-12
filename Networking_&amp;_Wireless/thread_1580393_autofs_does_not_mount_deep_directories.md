---
title: "autofs does not mount deep directories"
date: 2010-09-23
forum: Networking &amp; Wireless
---

### Post by gmermoud on 2010-09-23
Hello

I use Ubuntu 10.4 LTS, and I have a remote server that exports my home directory. I use autofs to automatically mount it. However, since a recent upgrade, it no longer works. Namely, it mounts the export/ directory, but when I try to access the enclosed directories, it returns the error: No such file or directory.

```

gmermoud-local@disalpc19:~$ cd /net/disalsrv1
gmermoud-local@disalpc19:/net/disalsrv1$ ls
export  export2
gmermoud-local@disalpc19:/net/disalsrv1$ cd export
bash: cd: export: No such file or directory
```I tried on a different server, and the same thing happened, but at one level deeper, i.e., i could enter in the export directory, but not in the directories it contains...

Thanks for your help,

Greg

---

### Post by gmermoud on 2010-09-28
As a workaround, I added the necessary folders to my fstab, and it worked of course. Now, interestingly, autofs works again, without changing anything to my configuration...

---

