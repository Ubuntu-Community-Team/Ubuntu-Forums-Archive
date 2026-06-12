---
title: "Sharing Options: Sharing service not installed"
date: 2011-05-24
forum: Networking &amp; Wireless
---

### Post by mAsTERpEE on 2011-05-24
This is really stupid. The author of nautilus-share checks if samba is working by trying to execute /usr/sbin/smbd if it fails then it assumes samba is not working. Took me hours to fix.

sudo chmod +x /usr/sbin/smbd

Shouldnt there be a linux function that checks for installed packages?

---

