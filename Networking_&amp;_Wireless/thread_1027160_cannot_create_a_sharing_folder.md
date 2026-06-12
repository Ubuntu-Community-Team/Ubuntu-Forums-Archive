---
title: "cannot create a sharing folder"
date: 2009-01-01
forum: Networking &amp; Wireless
---

### Post by reivan1 on 2009-01-01
every time i click the share this folder button i get this error.

[http://img4.uploadhouse.com/fileuploads/3246/3246464764274f4c2f13598e19aa1aa391f0e74.png](http://img4.uploadhouse.com/fileuploads/3246/3246464764274f4c2f13598e19aa1aa391f0e74.png)

anyhelp? please

---

### Post by Iowan on 2009-01-01
I'm doing a search for "net usershare". [Here]("http://www.prash-babu.com/2008/05/how-to-setup-samba-in-linux.html") is a thread that mentions making yourself a member of the smbusers group (or something similar). Another thing mentioned was making sure your user is a valid Samba user (created with **sudo smbpasswd -a username**)  A bug was mentioned [here]("http://ubuntuforums.org/showthread.php?t=825965").

---

