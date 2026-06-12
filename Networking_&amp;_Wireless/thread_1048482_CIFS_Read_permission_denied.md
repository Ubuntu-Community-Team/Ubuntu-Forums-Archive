---
title: "CIFS: Read permission denied"
date: 2009-01-23
forum: Networking &amp; Wireless
---

### Post by raghukiran1224 on 2009-01-23
Hi,
  I have a samba share that I am trying to mount from my local machine. I used the following command to do it: mount -t cifs //<server>/<share> ./<mount point> -o user=<uname>. The mount happens without any problems, but when I try to read any of the files (say cat <filename.txt>), it gives me a permission denied error. Strangely, I can write/create new files and even delete old ones (which I cannot read). Any idea where the problem is?

Thanks,
Raghu
p.s. I am using Ubuntu 8.10

---

### Post by Iowan on 2009-01-23
I presume you've seen [this]("http://ubuntuforums.org/showthread.php?t=288534") How-To.

---

### Post by raghukiran1224 on 2009-01-23
Thanks Iowan for your reply.

Yes, I did check that link. But, even when I gave the gid and uid parameters, it gave me the same errors. I checked my dmesg output and got the following:
" Status code returned 0xc0000022 NT_STATUS_ACCESS_DENIED
CIFS VFS: Send error in read = -13". Also, I tried to mount it as root on my local client machine with the same results.

My samba server is a 3.0 version and my client is 3.2. Does that cause any problem?

Thanks,
Raghu

---

