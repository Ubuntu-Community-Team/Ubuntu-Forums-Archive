---
title: "Network vs Connect to Server"
date: 2011-01-12
forum: Networking &amp; Wireless
---

### Post by Castarmax on 2011-01-12
Whats the difference? I would much prefer to connect via connect to network but I am unable. I can only connect via connect to server and typing in the other boxes ip address. All the other boxes see me just fine.

Thanks

---

### Post by PatchesTheCaveman on 2011-01-13
Try adding this line to the *[global]* section of /etc/samba/smb.conf
```
wins support = yes
```

---

### Post by Castarmax on 2011-01-13
Your the man Patches!!

---

