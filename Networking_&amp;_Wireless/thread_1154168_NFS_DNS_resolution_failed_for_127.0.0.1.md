---
title: "NFS DNS resolution failed for 127.0.0.1"
date: 2009-05-09
forum: Networking &amp; Wireless
---

### Post by indifference on 2009-05-09
Hello,

I'm implementing a NFS v2 server, and for testing it, I'm running the client on the same machine.

On Ubuntu 8.10, I just run the server and type:
sudo mount.nfs 127.0.0.1:/home/.pedro/spoint mpoint -o hard,intr,nfsvers=2

Now, on Ubuntu 9.04, if I'm NOT CONNECT TO INTERNET, I get:
mount.nfs: DNS resolution failed for 127.0.0.1: Name or service not known

If I'm CONNECTED, the mount is successful.

What I'm doing wrong?

Thanks,

Pedro Saraiva

---

