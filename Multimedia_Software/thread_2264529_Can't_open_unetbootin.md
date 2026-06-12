---
title: "Can't open unetbootin"
date: 2015-02-08
forum: Multimedia Software
---

### Post by josh109 on 2015-02-08
Whenever I try to open unebootin (version 494) (from terminal), I get the following error message:
./unetbootin-linux-494: error while loading shared libraries: libXi.so.6: cannot open shared object file: No such file or directory
 
I've tried running the command while root and using other versions yet still get the same error. Anyone know what can fix this?

---

### Post by sudodus on 2015-02-08
Are you running standard Ubuntu? Which version?

How did you install Unetbootin? From the repositories or from a deb file or some other way? If you uninstall your current version and reinstall the version from the repositories, it might start working.

Otherwise there are other tools to create USB boot drives. See this link

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

