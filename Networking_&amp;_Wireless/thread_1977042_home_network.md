---
title: "home network"
date: 2012-05-09
forum: Networking &amp; Wireless
---

### Post by 2-e on 2012-05-09
Trying to share files between laptop with ubuntu 12.04 and desktop with lubuntu 11.04.  I've searched the forums for a while but have gotten no further than installing open ssh. The desktop also has a fedora partition that i'd like to file share with lubuntu (same machine) and possible ubuntu. Any help would be greatly appreciated.

---

### Post by papibe on 2012-05-09
Hi 2-e.

You can the sftp url on both computers to access your files from the other computer:
```
sftp://youruser@remote_machine/home/youruser
```
That works on both file managers (Lubuntu's PCManFM and Ubuntu's Nautilus).

I hope that helps.
Regards.

---

### Post by 2-e on 2012-05-16
I wound up using ssh which is fine. I also tried personal file sharing and although I can see the other computer's public folder on my network I can't connect to it. Can't mount device message appears. Sftp now appears in the network column. I don't know which application caused it to appear. Thank you for your help.

---

