---
title: "Where is the foldder of GIMP"
date: 2024-02-22
forum: Multimedia Software
---

### Post by satimis on 2024-02-22
Hi all,

Ubuntu 22.04 desktop.

GIMP 2.10.30 was installed on repo

 apt policy gimp```

gimp:
  Installed: 2.10.30-1ubuntu0.1
  Candidate: 2.10.30-1ubuntu0.1
  Version table:
 *** 2.10.30-1ubuntu0.1 500
        500 http://hk.archive.ubuntu.com/ubuntu jammy-updates/universe amd64 Packages
        500 http://security.ubuntu.com/ubuntu jammy-security/universe amd64 Packages
        100 /var/lib/dpkg/status
     2.10.30-1build1 500
        500 http://hk.archive.ubuntu.com/ubuntu jammy/universe amd64 Packages

```

Please advise where is its folder.  I need to check whether following python plugins have been installed```

Restore1.py
Restore2.py
Restore3.py
```

Thanks

Regards

---

### Post by deadflowr on 2024-02-22
Should be in the ~/.config/GIMP/2.10/
should have a plugins folder.

---

