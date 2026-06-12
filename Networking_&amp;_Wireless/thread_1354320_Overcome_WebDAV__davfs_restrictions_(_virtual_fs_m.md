---
title: "Overcome WebDAV / davfs restrictions ( virtual fs maybe ) ?"
date: 2009-12-13
forum: Networking &amp; Wireless
---

### Post by Devport on 2009-12-13
I have 1TB of on-line backup storage that I would like to use to backup my video archive which contains dozens of movies up to a size of 10 GB ( all legally obtained by recording on tv ) on an ext3 partition. 

Since the on-line storage is limited to files < 500MB and its filenames are limited too compared to ext3 I wonder if anyone knows a trick to circumvent those limitations ( maybe by using a virtual file-system on top of davfs ).

---

### Post by Lars Noodén on 2009-12-14
You could try sshfs to transfer the files.  Or plain sftp.  You'll need openssh-server running on the remote machine first, plus an account there.

---

### Post by Devport on 2009-12-14
Thanks, but the on-line storage is only accessible via webdav.

---

