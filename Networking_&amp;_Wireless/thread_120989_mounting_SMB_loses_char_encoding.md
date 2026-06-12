---
title: "mounting SMB loses char encoding"
date: 2006-01-24
forum: Networking &amp; Wireless
---

### Post by borisattva on 2006-01-24
i succesfully mounted an smb folder to /mnt/library/music

this is my fstab line that does it well

```
//192.168.1.101/Music        /mnt/library/music  smbfs   credentials=/root/.smbcredentials,dmask=777,fmask=777   0       0
```

i am able to browse it through Nautilus, except files that originally contain accented characters (like è, ñ, etc) are somehow converted to lose the accents (into e, n respectively)

as such it becomes impossible for me to access those files/directories as when my pc makes a request for them as it sees them, they obviously dont exist,

on the other hand when i try to browse those same directoriess via network neighbourhood, all files display as they are.

why is this? what do i need to add into fstab to make the files appear as they are with no conversion?

---

### Post by adamkane on 2006-04-01
You can retain your character encoding if you browse, rather than mount:
 Places -> Connect to Server...
 
 You can mount, if you use the correct mount flags:
 mount -o nls=utf8 /share /folder
 
 If all else fails, you can convert your filename encodings after you transfer your files:
 [http://www.ubuntuforums.org/showthread.php?t=144297]("http://www.ubuntuforums.org/showthread.php?t=144297")
 ```

 sudo apt-get install convmv
 convmv -f cp850 -t utf-8 -r --notest *.*
 
```

---

### Post by ShiftyPowers on 2006-11-02
adamkane.

Thanks for your note on the convmv...that seems to work, annoying to have to do that everytime for most of the files.

---

