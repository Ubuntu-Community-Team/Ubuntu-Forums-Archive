---
title: "Curlftpfs vs. Sshfs?"
date: 2009-09-07
forum: Networking &amp; Wireless
---

### Post by moore.bryan on 2009-09-07
This *may* be a purely academic question, but which is "better" to use: curlftpfs or sshfs?

---

### Post by kotnik on 2009-09-07
I used both of them, and sshfs proved itself way better to use, so I'm using sshfs on all my hosts that have sftp support.

Curlftpfs is way too slow (it's not its problem, ftp is that kind of protocol), copying large ammount of small files can last forever, it lags when you edit a file, lots of hosts setup their ftp servers to be barely usable, etc.

If you can choose (sftp support on server), use sshfs.  My 2c...

---

### Post by moore.bryan on 2009-09-07
I've found the same... more with unreliability than speed, but still came to the same conclusion. Like I posted, this may be academic.

---

