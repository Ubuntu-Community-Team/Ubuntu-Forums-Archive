---
title: "Cifs mount moving files instead of copying"
date: 2009-01-24
forum: Networking &amp; Wireless
---

### Post by bsparkinson on 2009-01-24
Hi,

I'm using Ibex. I have an unRaid server with several shares. I mount some of these shares to /mnt/<somefolder> in /etc/fstab using :
```
//<server>/<share> /mnt/<somefolder> cifs username=###,password=###,_netdev,uid=###,gid=users 0 0
```

This all works fine and I can cruise around the share without a problem. However, when I click and drag a file into /home/<myuser>, for example, it sometimes moves the file instead of copying. 

Does anybody know what would cause this? I recently got burnt by it because I dragged the file, used it and deleted it. When I went to use the files again it wasn't there. This is the only time it happened, I've just copied a png image across and noticed it moved which prompted this message.

Thanks

---

