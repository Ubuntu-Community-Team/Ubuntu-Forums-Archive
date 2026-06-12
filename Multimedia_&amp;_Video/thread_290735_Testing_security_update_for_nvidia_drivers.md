---
title: "Testing security update for nvidia drivers"
date: 2006-11-01
forum: Multimedia &amp; Video
---

### Post by kees on 2006-11-01
Hello!

We'd like to get wider testing of the official nvidia drivers Ubuntu package.  If you still have the stock Dapper or Edgy nvidia drivers installed and want to help test the 8776 release, please read:

[https://lists.ubuntu.com/archives/ubuntu-devel/2006-November/022177.html](https://lists.ubuntu.com/archives/ubuntu-devel/2006-November/022177.html)

For Dapper, add..

  ```
deb http://people.ubuntu.com/~kees/test-lrm-2.6.15.12-1/ ./
```

For Edgy, add...

  ```
deb http://people.ubuntu.com/~kees/test-lrm-2.6.17.6-1/ ./
```

to your /etc/apt/sources.list, the new packages should show up after an "apt-get update".  Remember you must **reboot** after doing the "apt-get upgrade" or else X will not restart (since the new nvidia kernel module will not yet be loaded).

So far, everything has tested okay, but we want to make sure there haven't been any unnoticed regressions.

Thanks!

---

### Post by tseliot on 2006-11-01
I have been doing the same thing:
[http://ubuntuforums.org/showthread.php?t=255929](http://ubuntuforums.org/showthread.php?t=255929)

---

