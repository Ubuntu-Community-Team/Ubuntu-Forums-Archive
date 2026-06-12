---
title: "ati graphic drivers do not install properly"
date: 2012-05-18
forum: Multimedia Software
---

### Post by overrated on 2012-05-18
Hey,
i just tried to install the proprietary ati drivers for my Radeon HD 5850 like described [here]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")
However, after the reboot, when i insert
[PHP]fglrxinfo[/PHP]
i get
[PHP]X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  139 (ATIFGLEXTENSION)
  Minor opcode of failed request:  66 ()
  Serial number of failed request:  13
  Current serial number in output stream:  13
[/PHP]
Also, PlayOnLinux is reporting that it can't find the OpenGL Libraries any more.

Greetings
Mikrofonkabel

---

### Post by hobby boy on 2012-05-19
Have you tried manually installing the drivers and is your version of Ubuntu 32bit or 64bit?

---

### Post by vorbid on 2012-05-19
Hey man!  I had the same issue over a month ago when i first installed Ubuntu. Well what i did was, i recompiled the source from their official page and then had to --force the installation from the terminal in order for it to work. After the reboot i had the drivers installed. But i can tell you, i wasted over 5 hours to get it to work.   Hope this helped you.

---

### Post by roelforg on 2012-05-19
Please note that the post-release updates driver doesn't work.
Also, you need to reboot after the install to make it work

---

