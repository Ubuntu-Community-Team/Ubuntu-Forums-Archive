---
title: "File Share fail"
date: 2009-11-14
forum: Networking &amp; Wireless
---

### Post by Fir3chi3f on 2009-11-14
I tried to share a local disk on this machine and the first time it failed something along the lines of 'no testparm'. So I installed samba4-common-bin and fixed that problem but now I have this error:

```
Samba's testparm returned error 1: Loaded smb config files from --parameter-name=usershare allow guests
lp_load: refreshing parameters from --parameter-name=usershare allow guests
params.c:OpenConfFile() - Unable to open configuration file "--parameter-name=usershare allow guests":
	No such file or directory
Error loading services.
```

I also installed samba-config and starting up the program it says that there are unreadable lines and lists just about the whole config file.

---

### Post by Fir3chi3f on 2009-11-14
oops! looks like I solved my own problem. Installing samba-common-bin fix the problem

---

### Post by edunick on 2010-01-24
hay que reinstalar samba
[http://ubuntuforums.org/showthread.php?t=1326968](http://ubuntuforums.org/showthread.php?t=1326968)

---

