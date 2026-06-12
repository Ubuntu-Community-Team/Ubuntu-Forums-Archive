---
title: "add-apt-repository Error!"
date: 2010-06-09
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by QQi on 2010-06-09
```
$ sudo add-apt-repository ppa:xorg-edgers/ppa
/usr/lib/python2.6/dist-packages/softwareproperties/SoftwareProperties.py:114: DeprecationWarning: Attribute 'FindI' of the 'apt_pkg.Configuration' object is deprecated, use 'find_i' instead.
  value = apt_pkg.Config.FindI(softwareproperties.CONF_MAP[option])
/usr/lib/python2.6/dist-packages/softwareproperties/ppa.py:43: DeprecationWarning: Attribute 'FindDir' of the 'apt_pkg.Configuration' object is deprecated, use 'find_dir' instead.
  sourceslistd = apt_pkg.Config.FindDir("Dir::Etc::sourceparts")
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 165D673674A995B3E64BF0CF4F191A5A8844C542
gpg: requesting key 8844C542 from hkp server keyserver.ubuntu.com
gpg: key 8844C542: public key "Launchpad PPA for xorg crack pushers" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
```

:confused::confused:

---

### Post by zika on 2010-06-09
> **QQi said:**
> ```
$ sudo add-apt-repository ppa:xorg-edgers/ppa
/usr/lib/python2.6/dist-packages/softwareproperties/SoftwareProperties.py:114: DeprecationWarning: Attribute 'FindI' of the 'apt_pkg.Configuration' object is deprecated, use 'find_i' instead.
  value = apt_pkg.Config.FindI(softwareproperties.CONF_MAP[option])
/usr/lib/python2.6/dist-packages/softwareproperties/ppa.py:43: DeprecationWarning: Attribute 'FindDir' of the 'apt_pkg.Configuration' object is deprecated, use 'find_dir' instead.
  sourceslistd = apt_pkg.Config.FindDir("Dir::Etc::sourceparts")
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 165D673674A995B3E64BF0CF4F191A5A8844C542
gpg: requesting key 8844C542 from hkp server keyserver.ubuntu.com
gpg: key 8844C542: public key "Launchpad PPA for xorg crack pushers" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
```

:confused::confused:I do not see any error here. Just the log of successful ppa import along with its key...

---

### Post by questioning on 2010-06-09
it does the right things, but still theres the python error.

im also getting it.

---

### Post by zika on 2010-06-09
> **questioning said:**
> it does the right things, but still theres the python error.

im also getting it.You're right, I did not look right far enough. My mistake... Sorry...

---

### Post by Reiger on 2010-06-10
It is not an “error” but a “warning”. It is easy enough to fix manually: the warning spells out what you need to change to make the warning go away. ;)

---

