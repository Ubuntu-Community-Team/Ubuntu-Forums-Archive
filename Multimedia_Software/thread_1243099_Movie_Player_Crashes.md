---
title: "Movie Player Crashes"
date: 2009-08-17
forum: Multimedia Software
---

### Post by andrew13321 on 2009-08-17
Running .mp3, .avi, or anything, it just freezes and I have to force quit.

/var/lib/python-support/python2.6/gdata/tlslite/utils/cryptomath.py:9: DeprecationWarning: the sha module is deprecated; use the hashlib module instead
  import sha

That's the error I get.
Also it's not crashing, it's just skipping.

---

### Post by miegiel on 2009-08-18
> **andrew13321 said:**
> Running .mp3, .avi, or anything, it just freezes and I have to force quit.

/var/lib/python-support/python2.6/gdata/tlslite/utils/cryptomath.py:9: DeprecationWarning: the sha module is deprecated; use the hashlib module instead
  import sha

That's the error I get.
Also it's not crashing, it's just skipping.

Check for updates *System > Administration > Update Manager*

or
```

sudo apt-get update
sudo apt-get upgrade
```

if packages are being held back try

```
sudo apt-get dselect-upgrade
```

---

