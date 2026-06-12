---
title: "Mounting Samba share with space, \040 not working?"
date: 2011-01-23
forum: Networking &amp; Wireless
---

### Post by shimrodmimir on 2011-01-23
I've been having trouble auto-mounting shared on my NAS from Ubuntu. As the folders have spaces in them, and I got a mount error(6) returned, I ran some tests to see if the issue was related to these spaces. It seems to be:

I shared my music folder on my ubuntu PC as 'music' and mounted is from my laptop using ```
sudo mount -t cifs //192.168.2.102/music /media/test
``` This worked flawlessly.

I then renamed the share on the PC to 'my music' and tried to mount it again using ```
sudo mount -t cifs //192.168.2.102/my\040music /media/test
``` Strangely enough I got the mount error(6): no such device, indicating that it now could not resolve the share name.

I really don't understand what I'm doing wrong here, all the guidance I read indicates that substituting spaces with \040 should do the trick. Thoughts anyone?

---

### Post by shimrodmimir on 2011-01-25
No one any ideas why I can't mount samba shares with spaces using \040 ?

---

### Post by luvshines on 2011-01-26
Doesn't \040 works only for 'fstab' entries ?

---

### Post by Morbius1 on 2011-01-26
Spaces in names always confuse me. You're never sure if it's "\040", "\ ", "%20", or none of the above. As luvshines stated I always use "\040" in fstab.

In this case I think it's none of the above. Try this:
```
 sudo mount -t cifs //192.168.2.102/"my music" /media/test
```

---

