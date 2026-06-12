---
title: "How to setup vsftpd"
date: 2008-12-10
forum: Networking &amp; Wireless
---

### Post by rado3105 on 2008-12-10
Hi, I installed vsftpd. I want to change directory /home/ftp to /media/disk(or make some link to that point when somebody log to ftp).
Also I want to use anonymous enter to that ftp server for local users(and make there some folder /media/disk/upload for anonymous users from my local network to upload there).
I want for that server to allow writing there only one user, also using password e.g: johny.
And one account for users outside my network, to use name: internet(they can read from that server, but first must use name: internet and password to log there).

---

### Post by superprash2003 on 2008-12-10
use gproftpd instead .. easy to configure sudo apt-get install gproftpd.

---

