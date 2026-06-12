---
title: "wicd - permission denied"
date: 2011-05-21
forum: Networking &amp; Wireless
---

### Post by mapreduced on 2011-05-21
Hello guys,

I am running VMPlayer on Windows 7 and installed Ubuntu 10.10 on it. I wanted to enable wifi. So I took following steps after googling different ways:
-Downloaded wicd 1.7 on windows and copied it over to ubuntu
-ran  sudo python setup.py configure and sudo python setup.py install from correct directories
-restarted dbus (as it was mentioned in readme)
-restarted ubuntu
-tried to open wicd network manager from application>internet
ERROR: Failed to execute child process "wicd-gtk" (Permission denied)

I just don't know which directories to provide permissions to!!

I tried "find / '*wicd*' " to find all wicd related files so that I could provide 755 permission to them, but not much help :(.

---

### Post by mapreduced on 2011-05-27
I also tried to use Wired Connection and it was not working for some reason. Then I started to suspect if my NAT is working at all in VMWorkStation? It wasn't.
Cause: When I upgraded from Vista to Windows 7, VMWare went berserk.
Solution: Reinstall VMWorkstation :) and now all is well
:guitar:

---

