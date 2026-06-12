---
title: "Shh Connection"
date: 2012-03-03
forum: Multimedia Software
---

### Post by Bray90820 on 2012-03-03
for some reason i cant connect to my ubuntu server with an ssh client but if i use the terminal it connects right away

---

### Post by Toz on 2012-03-09
Are you running both locally or is the ssh attempt from a remote system? If remote, is there a firewall blocking the attempt? This command will show the status of your firewall:
```
sudo ufw status verbose
```

Otherwise, can you provide some more information?

---

