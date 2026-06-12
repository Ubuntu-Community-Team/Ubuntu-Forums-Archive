---
title: "How to set Samba to start at boot time"
date: 2009-09-14
forum: Networking &amp; Wireless
---

### Post by swerdna on 2009-09-14
In Ubuntu I goto the Panel and click System --> Administration --> Services and enable File Sharing (Samba) to cause Samba to be always on.

What do I do in Xububtu to achive that.

Thanks
swerdna

---

### Post by uncle-c on 2009-09-14
I use a program called sysv-rc-conf which you can get from the repositories and which is very easy to use from a command line terminal.
You will have to make sure smb and nmb daemons start at boot

---

### Post by swerdna on 2009-09-14
Thanks very much. It works easily and well for Samba

---

