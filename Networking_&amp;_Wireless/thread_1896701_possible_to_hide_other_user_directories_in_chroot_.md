---
title: "possible to hide other user directories in chroot sftp?"
date: 2011-12-17
forum: Networking &amp; Wireless
---

### Post by unyalli on 2011-12-17
Hello,
  Running 10.04 LTS
I have an openssh sftp server chrooting users to a root sftp directory and verbosely logging all activity. I have restricted user1 from accessing user2's directory. Can I hide user2's directory so user1 won't even attempt going there?

Detail if interested;
Everyone chroots to /home/sftproot then cd's into their dir.
This is so I only have one unixsocket for logging.
user directories are chmod 750 and owner=user group=root

As stated they can't access the other user directories but they can see them. I'd like to hide them.

Thanks, Jeff

---

