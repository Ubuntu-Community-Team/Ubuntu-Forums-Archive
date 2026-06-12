---
title: "Owner/Group IDs incorrect with mounted share"
date: 2009-03-27
forum: Networking &amp; Wireless
---

### Post by khm on 2009-03-27
I'm mounting a windows share via smbmount and the owner and group ids are just listed as 4 digit numbers, even items which I know I am the owner of.  

```
sudo mount -t cifs //afrog.ap.lexmark.com/firmwaretestlex firm/ -o username=kmonday,password=********,iocharset=utf8,file_mode=0777,dir_mode=0777
```

```
sudo smbmount //afrog.ap.lexmark.com/firmwaretestlex firm/ -o username=kmonday,password=********,iocharset=utf8,file_mode=0777,dir_mode=0777
```

Any ideas on how I can fix this?

---

### Post by khm on 2009-04-15
..bump

---

