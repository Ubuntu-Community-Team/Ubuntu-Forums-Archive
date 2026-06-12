---
title: "Combined SFTP/FTP Server - permissions nightmare!"
date: 2009-07-22
forum: Networking &amp; Wireless
---

### Post by iandol on 2009-07-22
Hi, I've been fighting for days to try to do what was trivial on my previous XP server - have one storage directory which allows a user to SFTP or FTP into, and read/write without chance to traverse out of that directory (chrooted). 

The storage harddisk is NTFS formatted (lots of data on it already) as I need to read it from windows occasionally.

I wanted to use virtual users for the FTP side. ProFTPd just never authenticated properly, and neither did PureFTPd (following whatever tutorials i could find). I finally managed to get vsftpd to work wonderfully with virtual users. Lovely and fast too. I use the uid/gid options in fstab to allow the virtual user write access.

So then i move on to setting up opensshd - only to find I can **only** chroot when root owns the drive. As it is ntfs formatted (ntfs-3g for write), it appears i cannot change the subdirectory user:groups with ntfs-3g (only global uid/gid on mount) and thus I cannot now write to the drive with my SFTPed user. And anyway the user/group are now different between vsftpd and sshd.

Does anyone know of a better solution to this? Is there a way to get openssh to ignore permissions? 

I think I'll give a commercial solution like CrushFTP a go, though initial tests showed it had crummy ubuntu support.

---

### Post by iandol on 2009-08-05
As an update: CrushFTP has a very helpful and powerful UI. You can do a lot more fine-grained control of users and resources than ever opensshd and pure/vsftpd allow. Sadly, the performance of the SFTP portion was ~10X slower than I obtained under openssh. So my solution is to remove FTP as an option, and just use openssh SFTP with chrooted users.

---

### Post by dmizer on 2009-08-05
I think your permissions problems are related to your NTFS drive mount. You may be interested in this thread: [http://ubuntuforums.org/showthread.php?p=7734629](http://ubuntuforums.org/showthread.php?p=7734629)

---

