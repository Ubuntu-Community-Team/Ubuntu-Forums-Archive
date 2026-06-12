---
title: "Permissions and NFS"
date: 2012-06-12
forum: Networking &amp; Wireless
---

### Post by shredator on 2012-06-12
hello, I am having 2 problems

1) I have an NFS share with the following options in /etc/exports: rw,sync,all_squash,anonuid=1003,anongid=1003,no_subtree_check.
the share is owned by the 1003 group, and the permissions are 770.  I am trying to use the directory from a windows 7 machine.  I am able to mount the share, but permission to view is denied.  The baffling part is that when I change the permissions of the share to 777, I can then use the share on the windows machine.  If I create a file in the share using the windows machine, the file will be shown as owned by the 'squashed' user and group, as it should.  I cant figure out why the client needs full permissions to be granted access to the share.

2) Once I get the mess above worked out, I would like files created by nfs clients in the share to be created with 770 permission.  I added 'umask 007' to the 1003 user's .profile file, but this has been without effect.  New files are still created with 755 permissions.  Is there a better way to do this with NFS?

Thanks for reading my post,
Cheers

---

