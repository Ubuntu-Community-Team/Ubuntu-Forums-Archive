---
title: "MythBuntu weekly updates"
date: 2008-01-17
forum: Mythbuntu
---

### Post by menny on 2008-01-17
Hi,
I have two questions regarding MythBuntu Weekly Updates:
1) What is the latest version? I have 0.20.2+fixes14681-0ubunu0~mythbuntu1
2) It seems that MythMusic can not be selected for updates. I have it (MythMusic) in the Update Manager list but I can not check it for update.

Thanks

---

### Post by AshtonBRSC on 2008-01-28
1)The latest version is 0.20.99+trunk15578-0ubuntu0~mythbuntu1

2)MythMusic is updating fine for me.

---

### Post by menny on 2008-01-28
Any idea why it is not updating to me?

---

### Post by superm1 on 2008-01-28
> **menny said:**
> Any idea why it is not updating to me?
Try updating it from a command line like this:

```
sudo apt-get dist-upgrade
```

It may have additional dependencies now.

---

### Post by Nikas on 2008-01-28
How can i see wich weekly build (trunk version)  i have installed?

---

### Post by superm1 on 2008-01-28
```
dpkg -l | grep myth
```

---

