---
title: "Mythfrontend Alt-F4"
date: 2009-11-13
forum: Multimedia Software
---

### Post by ForgivenByJC on 2009-11-13
Hi, has the functionality of the Alt-F4 key press been removed from mythfrontend?  I upgraded from 9.04 to 9.10 and Alt-F4 stopped responding.  Perhaps there is a new setting somewhere for this?  If so, I have not been able to locate it.  Thanks in advance for any and all help.
```
john@Sonja:~$ apt-cache policy mythtv-frontend 
mythtv-frontend:
  Installed: 0.22.0+fixes22594-0ubuntu1
  Candidate: 0.22.0+fixes22594-0ubuntu1
  Version table:
 *** 0.22.0+fixes22594-0ubuntu1 0
        500 http://archive.linux.duke.edu karmic/multiverse Packages
        100 /var/lib/dpkg/status
john@Sonja:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 9.10
Release:	9.10
Codename:	karmic
```

---

### Post by ForgivenByJC on 2009-11-19
This also happens with a fresh install of Ubuntu Karmic Koala 9.10.  Still no resolution.  Perhaps this has to do with the master backend?

---

### Post by ForgivenByJC on 2009-12-14
Still an issue.

---

### Post by plj on 2009-12-16
Hello ForgivenByJC,

have you reported this as a bug yet? I'm just asking, as I'm suffering from the same problem and considering reporting it.

The ALT+F4 works, if window borders have been turned on  under Utilities/Setup->Setup->Appearance->“Use window border”, but not otherwise.

---

### Post by ForgivenByJC on 2009-12-16
No, I have not reported it as a bug.  I think it would be a good idea.  You might get a better response than I have, so why don't you report it as a bug?
John

---

