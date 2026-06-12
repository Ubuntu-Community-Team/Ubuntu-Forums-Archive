---
title: "Blank CD not recognized"
date: 2009-11-20
forum: Multimedia Software
---

### Post by -Root- on 2009-11-20
Hello  guys i am using Ubuntu 9.10 and i am having this odd problem. Blank cd's are not begin recognized at all. I tried about 12 CD's DVD and CD-R none work. I tried putting CD's with content and they work great. I am also trying to use K3b to burn cd's and i get this error 

```
K3b is unable to detect your drive you need to change premission to give write access to device.  
```

Then i got another error with one of the CD's

```
Error mounting: mount exited with exit code 32: mount: block device /dev/sr0 is write-protected
```

then i tried

```
 sudo chmod 777 /dev/sr0/
```

Noting worked.

---

### Post by ilil on 2009-11-20
Maybe your problem is similar to [http://ubuntuforums.org/showthread.php?t=1331112](http://ubuntuforums.org/showthread.php?t=1331112).

And see more here: [https://bugs.launchpad.net/linux/+bug/464134](https://bugs.launchpad.net/linux/+bug/464134)

---

