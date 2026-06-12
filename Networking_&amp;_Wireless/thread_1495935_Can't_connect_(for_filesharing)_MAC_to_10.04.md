---
title: "Can't connect (for filesharing) MAC to 10.04"
date: 2010-05-28
forum: Networking &amp; Wireless
---

### Post by un207 on 2010-05-28
Hey everyone,

I desperately need to be able to connect my mac (and everyone else's mac in the workplace) to Ubuntu 10.04 - does anyone have ANY suggestions?! I'm not super savvy with Ubuntu/Linux - just enough to get in trouble.

Any help would greatly be appreciated!

---

### Post by jlb1717 on 2010-06-21
Hi,

I'm having the same issue (almost). I have been able to connect using my Windows machine without any problems.

I can also connect and view files (including streaming a movie for example) on my Mac but I can't modify or create files on the shared folder. Anyone got any suggestions?

I set it up by right clicking on the folder I wanted to share, set the folder permissions to share the folder, and all the folder options are set to create and save files. I can't seem to get it to do the same for files though.

Hope someone can help.

jlb1717

---

### Post by Morbius1 on 2010-06-21
Post the output of these commands so we can see how they are set up:
```
net usershare info
sudo net usershare info
```

---

