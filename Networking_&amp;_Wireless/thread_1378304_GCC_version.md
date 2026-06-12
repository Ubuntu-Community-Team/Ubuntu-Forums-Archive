---
title: "GCC version?"
date: 2010-01-11
forum: Networking &amp; Wireless
---

### Post by drpjkurian on 2010-01-11
Hi everybody

I found the following instruction in the "install" file of Madwifi 

```
gcc of same version that was used to compile the kernel.  At least
  make sure that the first two version numbers or the compiler are the
  same (e.g. it's OK to use gcc 3.4.6 to compile MadWifi if the kernel
  was compiled by gcc 3.4.2).  Ignoring this rule will cause "Invalid
  module format" errors during module load.
```

How can I implement this instructions.

With regards
Dr Kurian

---

### Post by drpjkurian on 2010-01-11
hi 
I got the answer
1. To know the version of gcc, type```
gcc -v
```

2. To know the version of gcc in which kernel was compiled can be known by
```
cat /proc/version
```

---

