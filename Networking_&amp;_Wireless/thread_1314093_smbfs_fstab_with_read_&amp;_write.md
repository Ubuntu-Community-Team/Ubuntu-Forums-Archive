---
title: "smbfs fstab with read &amp; write"
date: 2009-11-04
forum: Networking &amp; Wireless
---

### Post by readycarpenter on 2009-11-04
before upgrading to 9.10 I used this line to mount my windows shares

//mediaportal-htpc/media  /mnt/media  cifs  user=user,pass=password,uid=1000,gid=100  0  0


but now after upgrade to 9.10 can only read, nothing has changed on the windows box, but I can get write if I mount from >Places>Connect to Server...  and use the same user and password... did 9.10 change something in smbfs?

any help appreciated.

Ubuntu 9.10 rules!!

---

### Post by readycarpenter on 2009-11-05
duh, I need to set permissions on the mount directory, problem solved :)

---

### Post by cortexed on 2009-11-05
How exactly did you change the permissions?
Thanks

---

