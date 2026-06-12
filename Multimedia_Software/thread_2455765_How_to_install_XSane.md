---
title: "How to install XSane"
date: 2020-12-27
forum: Multimedia Software
---

### Post by satimis on 2020-12-27
Hi all,

Ubuntu 20.04 desktop

Please advise the correct way to install XSane

I have sane, sane-untility xsane installed.

$ apt policy sane```

sane:
  Installed: 1.0.14-15
  Candidate: 1.0.14-15
  Version table:
 *** 1.0.14-15 500
        500 http://hk.archive.ubuntu.com/ubuntu focal/universe amd64 Packages
        100 /var/lib/dpkg/status
```
        
$ apt policy sane-utils```

sane-utils:
  Installed: 1.0.29-0ubuntu5.2
  Candidate: 1.0.29-0ubuntu5.2
  Version table:
 *** 1.0.29-0ubuntu5.2 500
        500 http://hk.archive.ubuntu.com/ubuntu focal-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     1.0.29-0ubuntu5.1 500
        500 http://security.ubuntu.com/ubuntu focal-security/main amd64 Packages
     1.0.29-0ubuntu5 500
        500 http://hk.archive.ubuntu.com/ubuntu focal/main amd64 Packages

```

$ apt policy xsane```

xsane:
  Installed: 0.999-8ubuntu2
  Candidate: 0.999-8ubuntu2
  Version table:
 *** 0.999-8ubuntu2 500
        500 http://hk.archive.ubuntu.com/ubuntu focal/universe amd64 Packages
        100 /var/lib/dpkg/status

```
        
But unable to install libsane-extras or libsane-extras-common

$ apt policy libsane-extras```

N: Unable to locate package libsane-extras

```

$ apt policy libsane-extras-common```

N: Unable to locate package libsane-extras-common

```

XSane can't be started correctly.  Pls see attached screenshot.

Please help.  Thanks

Regards

---

### Post by Holger_Gehrke on 2020-12-27
On my XUbuntu 18.04 libsane-extras contains additional backends which were not yet included with sane at the time. Those are backends for the Genius ColorPage Vivid Pro II and Nikon LS-5000 ED / Coolscan 5000 ED. libsane-extras-common holds documentation for these backends. In 20.04 the packages don't exist and I can't find those backends in the list of files for libsane, so they were either dropped or rolled into some of the other backends.

Could you please describe what's wrong with xsane since the screenshot looks OK to me.

Holger

---

### Post by satimis on 2020-12-27
Hi Holger,

Thanks for your advice

I can't scan film negatives.  The preview shows the film holder with negative strip mounted on it, looking similar to scanning doc.  Whether I need to run GIMP to scan film negatives.? If Yes, please advise how.  Thanks

Regards

---

### Post by satimis on 2020-12-28
Hi Holger

Problem solved.

Next to scanner icon, select [Transparency Adapter]
then I can scan negatives.

But the images are too dark.  Where should I adjust?

Regards

---

