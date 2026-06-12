---
title: "Different Versions of alsa-base and asound"
date: 2011-05-03
forum: Multimedia Software
---

### Post by karmila on 2011-05-03
This morning i ran this command to check installed alsa-driver.
```
ari@Natty:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version **1.0.23.**
```
It says 1.0.23 version of alsa driver.

But when I check alsa-base package it tells different version.
```
ari@Natty:~$ dpkg --status alsa-base
Package: alsa-base
Status: install ok installed
Priority: optional
Section: sound
Installed-Size: 516
Maintainer: Ubuntu Core Developers <ubuntu-devel@lists.ubuntu.com>
Architecture: all
Source: alsa-driver
Version: **1.0.24**+dfsg-0ubuntu1
Provides: alsa
Depends: lsof (>= 4.64), module-init-tools (>= 3.2.1), linux-sound-base, udev
Recommends: alsa-utils
Suggests: apmd (>= 3.0.2-1), alsa-oss, oss-compat
Conflicts: alsa-utils (<< 1.0.9a-4), discover (<< 2.0.7-1), discover1 (<< 1.7.3), lsof-2.2 (<< 4.64), modutils (= 2.3.20-1)
...............
...............
...............

```
alsa-base 1.0.24 is installed.

Is that what it should looks be, or there is something wrong?

---

### Post by lidex on 2011-05-04
Yeah I get that too. As long as it works, I wouldn't worry about it.

---

