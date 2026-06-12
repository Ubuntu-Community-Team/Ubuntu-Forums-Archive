---
title: "High sshd CPU usage during sftp transfers"
date: 2012-09-14
forum: Networking &amp; Wireless
---

### Post by HunterZ on 2012-09-14
I'm running Xubuntu 12.04 x64 on an AMD 64 X2 4200 dual core 2.2GHz machine. I'm connecting to it via SFTP from my Windows machine over my 100mbps LAN, using FileZilla. I noticed that when I transfer large files, sshd consumes a lot of CPU time:


[LIST]
[*]1 transfer: Pegs one of my CPU cores at 100% and I only get around 80mbps transfer speed.
[*]2 transfers: Two sshd processes running at ~60% CPU usage each, and my transfer speed reaches the full 100mbps.
[*]3 transfers: Three sshd processes run at around ~45% CPU usage, and the transfer speeds seem to jitter whenever other processes need CPU time (I actually saw as low as 60mbps when I had something else CPU-intensive going on at the same time, which is what prompted me to post here).
[/LIST]

Are there any sshd/sftp settings I can tweak on the Xubuntu end to reduce CPU usage?

I'm running an NFS server on the Windows machine, so I suppose I should probably just set up a mount to that on the Xubuntu machine and push the files across. I don't like using Samba because it seems to have transport overhead that often keeps it from getting close to 100% bandwidth utilization as well.

---

### Post by lukeiamyourfather on 2012-09-14
EDIT: Accidental double post.

---

### Post by lukeiamyourfather on 2012-09-14
SFTP is encrypted using SSH (i.e. the sshd). Not using SFTP and just using FTP would improve performance. If simply mounting the share if you're on a local network is a much better option than SFTP.

---

