---
title: "cifs having trouble deleting very large files"
date: 2009-04-26
forum: Networking &amp; Wireless
---

### Post by SimonProven on 2009-04-26
I'm backing up using sbackup to a samba share and having problems with the purge process - it only goes wrong once a month deleting a month old backup hence it's taken me a while to work out what's going on.

It turns out that I can't delete files (using rm -r) which are very large, over 2 gigabytes in size.  If I try this, then the rm gets an error even though the file was actually deleted, and thus the delete doesn't complete.

Has anyone else seen this kind of behaviour? I'm on 8.04.

Example output:

simon@librarian:/mnt/mybook/librarian-backup$ rm -r 2008-*.inc
rm: cannot remove `2008-09-03_04.00.04.247033.librarian.inc/files.tgz': No such file or directory
rm: cannot remove `2008-09-04_04.00.03.209325.librarian.inc/files.tgz': No such file or directory

Retrying the operation finishes the job as the removed files really have been deleted.

---

