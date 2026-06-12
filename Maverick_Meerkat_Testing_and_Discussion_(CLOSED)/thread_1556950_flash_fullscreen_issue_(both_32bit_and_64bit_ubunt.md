---
title: "flash fullscreen issue (both 32bit and 64bit ubuntu)"
date: 2010-08-20
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by yelo3 on 2010-08-20
Hello, I recently reinstalled ubuntu and choose the 32bit version because I previously had a problem in the 64bit install: when switching to fullscreen, the flash animation video would stop working, and I could only hear sound.

Do you have this problem too?

---

### Post by go7Ul1ai on 2010-08-20
This has always been an issue for me since I started using Ubuntu (7.10) ^_^

---

### Post by lovinglinux on 2010-08-20
[http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html](http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html)

---

### Post by Roosje on 2010-08-22
Hey, thank you very much! That fixed my flash fullscreen troubles.

sudo mkdir /etc/adobe
echo "OverrideGPUValidation=true" >~/mms.cfg
sudo mv ~/mms.cfg /etc/adobe/

Worked like a charm, no idea why but it did.

---

