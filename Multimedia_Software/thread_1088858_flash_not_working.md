---
title: "flash not working"
date: 2009-03-06
forum: Multimedia Software
---

### Post by heiNey on 2009-03-06
im trying to get youtube videos to work, but it says flash isnt installed...ive already installed it, but if i try to click on the 'install missing plugins' in firefox anyway, it says its already installed.

i tried the fix here: [http://ubuntuforums.org/showthread.php?p=3923465](http://ubuntuforums.org/showthread.php?p=3923465) but it doesnt seem to do anything...still the exact same problem..anybody know how to fix this?

this is a fresh install of Hardy Heron 8.04

output from apt-cache policy

```


 sudo apt-cache policy flashplugin-nonfree
flashplugin-nonfree:
  Installed: 10.0.1.218+10.0.0.525ubuntu1~hardy1+really9.0.124.0ubuntu2
  Candidate: 10.0.1.218+10.0.0.525ubuntu1~hardy1+really9.0.124.0ubuntu2
  Version table:
 *** 10.0.1.218+10.0.0.525ubuntu1~hardy1+really9.0.124.0ubuntu2 0
        100 /var/lib/dpkg/status
     9.0.159.0ubuntu1~hardy1 0
        500 http://us.archive.ubuntu.com hardy-updates/multiverse Packages
        500 http://security.ubuntu.com hardy-security/multiverse Packages
     9.0.124.0ubuntu2 0
        500 http://us.archive.ubuntu.com hardy/multiverse Packages


```

---

### Post by heiNey on 2009-03-06
nevermind...looks like if you do it 5 times, itll work

---

