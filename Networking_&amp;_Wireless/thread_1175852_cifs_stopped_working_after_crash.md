---
title: "cifs stopped working after crash"
date: 2009-06-01
forum: Networking &amp; Wireless
---

### Post by snkiz on 2009-06-01
I was moving some files on a network drive any my computer locked up. after I rebooted my server could not mount samba shares from desktop but I can still mount samba shares from my server on my desktop, no errors in the logs that I could find, and tiring to remount with ```
sudo mount -a -t cifs
``` produces nothing. here is the cifs line in fstab from my server that worked fine before:
```
\\192.168.0.100\public  /home/media/Public  cifs  credentials=/etc/samba/users,setgid=media,file_mode=0777,dir_mode=0777 0 0
```
I don't have a clue dmesg says nothing and I don't know where else to look.

---

