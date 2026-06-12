---
title: "Maximum Of 1024 File Descriptor Limit"
date: 2013-08-27
forum: Networking &amp; Wireless
---

### Post by sajil2 on 2013-08-27
how to increase [h=1]Maximum Of 1024 File Descriptor Limit[/h]
i read so many posts.but they all confuse me.please tell me easiest way to increase this.where are my server out put.
ulimit -Sn
1024

---

### Post by bkline on 2013-08-28
Edit /etc/security/limits.conf as root [1] and add the following lines:

* soft nofile 2048
* hard nofile 2048

Replace 2048 with whatever value you need.

[1] Open a command console and enter "sudo nano /etc/security/limits.conf" (without the quote marks).

---

### Post by sajil2 on 2013-08-28
thanks for replay i followed your instructions but it still says 1024?

---

