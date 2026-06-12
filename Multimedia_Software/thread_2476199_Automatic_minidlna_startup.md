---
title: "Automatic minidlna startup"
date: 2022-06-19
forum: Multimedia Software
---

### Post by cperciba on 2022-06-19
I can view media on my smart tv only typing on command line 
"sudo service minidlna force-reload".


I tried to fix the issue editing rc.local :
--------------------------------------------------------------
claudio@SOLE:~$ cat /etc/rc.local
service minidlna force-reload
--------------------------------------------------------------


No success.


Could you help me please ?


--------------------------------------------------------------
claudio@SOLE:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description: Ubuntu 21.04
Release: 21.04
Codename: hirsute
--------------------------------------------------------------


Thanks !


Claudio

---

### Post by Xian on 2022-06-19
Can you post the contents of your /etc/minidlna.conf file?

---

