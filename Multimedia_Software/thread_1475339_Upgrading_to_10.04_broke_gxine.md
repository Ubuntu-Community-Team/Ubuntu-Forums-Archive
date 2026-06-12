---
title: "Upgrading to 10.04 broke gxine"
date: 2010-05-06
forum: Multimedia Software
---

### Post by epicoder on 2010-05-06
After upgrading to 10.04, gxine always fails with exit code 127 and this error:
```
gxine: error while loading shared libraries: libmozjs.so: cannot open shared object file: No such file or directory
```
I tried to install the package 'libmozjs0d', but apt-get failed with this error:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libmozjs0d is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libmozjs0d has no installation candidate
```

---

### Post by Yellow Pasque on 2010-05-06
I got the same thing. I had to:
```
sudo ln -s /usr/lib/firefox-3.6.3/libmozjs.so /usr/lib
sudo ldconfig
```

---

### Post by matthewbpt on 2010-05-06
I can confirm this behaviour. Maybe you should make a bug report on launchpad?

---

### Post by Yellow Pasque on 2010-05-07
> **matthewbpt said:**
> I can confirm this behaviour. Maybe you should make a bug report on launchpad?
Already there: [https://bugs.launchpad.net/ubuntu/+source/gxine/+bug/130218](https://bugs.launchpad.net/ubuntu/+source/gxine/+bug/130218)

---

### Post by epicoder on 2010-05-07
> **Temüjin said:**
> I got the same thing. I had to:
```
sudo ln -s /usr/lib/firefox-3.6.3/libmozjs.so /usr/lib
sudo ldconfig
```

Thanks, this worked for me.

---

