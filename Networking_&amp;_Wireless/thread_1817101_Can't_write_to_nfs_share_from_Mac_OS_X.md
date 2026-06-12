---
title: "Can't write to nfs share from Mac OS X"
date: 2011-08-02
forum: Networking &amp; Wireless
---

### Post by GROwen on 2011-08-02
Hi all,

I'm getting some strange behavior when trying to create directories on an nfs share on a linux machine that I'm accessing from Mac OS X 10.4.

I can copy files but cannot create new files or directories.

I've given every directory and file that's in the share directory rwx access for groups, users and owner and changed user to 777

The line I've added to my /etc/exports file is;

```
/home/Music 10.1.1.1/24 (rw,async,no_subtree_check,insecure)
```

Anyone have any suggestions on how I can start trouble shooting this? If I can copy a file why can't I create a new file/directory?

Thanks in advance for any help with this.

---

### Post by fuzzyworbles on 2011-08-03
it's because the user id that owns the share server side is not the same id on osx. the solution is to add 'all_squash' and 'anonuid={the user's id that owns the share}' to the export options.

---

### Post by GROwen on 2011-08-03
Thanks for the advice, it's now working exactly how I was hoping it would.

I'm going to have to learn more about permissions in linux...so glad there's this community.

---

