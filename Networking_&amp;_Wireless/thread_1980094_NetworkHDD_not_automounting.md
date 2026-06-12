---
title: "NetworkHDD not automounting"
date: 2012-05-14
forum: Networking &amp; Wireless
---

### Post by ChaosTage on 2012-05-14
hey guys!

i have tried automounting a usb drive in ubuntu that is connected to the usb port of my router. strangely it doesnt automount but when i mount it manually via the gui or tty it goes without problems. i already added this code to the fstab file

```
//speedport.ip/linux /mnt/NetworkHDD cifs auto,iocharset=utf8,uid=linuxbox,gid=users,credentials=/root/.cifscredentials,file_mode=0775,dir_mode=0775 0 0
```so basically i have a cifs credentials file in /root. but i dont understand why this still wont work. any ideas?

---

### Post by ChaosTage on 2012-05-21
sorry guys i got the answer but forgot to post it here.

i put the credentials file in /root but my account didnt have access to that folder without sudo so that was basically the problem. now it works all flawlessly except my laptop doesnt automatically turn off anymore when i shut it down, be it via terminal or gui. do i need to unmount my network hdd before shutdown or could this be another problem?

---

