---
title: "cannot install mplayer; 8.04 Hardy Heron; unmet dependencies"
date: 2009-04-12
forum: Multimedia Software
---

### Post by ieee488 on 2009-04-12
Here's the error message
> The following packages have unmet dependencies:
  mplayer: Depends: libpango1.0-0 (>= 1.20.5) but 1.20.1-1 is to be installed
E: Broken packages


I have no idea what that means. I've enabled everything in Software Sources.

---

### Post by mc4man on 2009-04-12
Go to System -> Admin... -> Software Sources -> Updates and make sure the first 2 boxes are checked (hardy-security, hardy-updates

If hardy-updates wasn't checked then enable, click close and reload. Then try again.

If both were checked then run in a terminal
```
sudo apt-get update 
```

libpango1.0-0 (1.20.5) is the updated hardy version

[http://packages.ubuntu.com/hardy-updates/libpango1.0-0](http://packages.ubuntu.com/hardy-updates/libpango1.0-0)

---

### Post by ieee488 on 2009-04-12
Hi,

Thanks that worked.

I didn't have the second checkbox in the Updates checked, so once I did that, Ubuntu installed a new kernel. Then I was able to get mplayer.

---

