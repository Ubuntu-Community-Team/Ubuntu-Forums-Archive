---
title: "Samba deleting mount directories"
date: 2008-05-08
forum: Mythbuntu
---

### Post by CleverJake on 2008-05-08
Ive been tryin for a day now to stream media from my windoze box to my mythbox, and I am stuck

I run

```
sudo mkdir /mnt/media
```

and the media folder is created, but then, once i run 
```
sudo mount -t cifs //Win_Dows/D/Media /mnt/media -o username=*****,password=*****,iocharset=utf8,file_mode=0777,dir_mode=0777
```

it does the weirdest thing, it seems like it mounts, but when the /mnt/media is clicked on, it says that the files doesn't exist, and that it may have been recently deleted.

It wont let me remove the file, or recreate one. This happens every time I try to mount it, wether I go by local ip or netbios name.


please help

---

