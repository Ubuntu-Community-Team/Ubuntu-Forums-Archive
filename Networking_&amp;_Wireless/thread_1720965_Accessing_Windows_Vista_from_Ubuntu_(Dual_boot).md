---
title: "Accessing Windows Vista from Ubuntu (Dual boot)"
date: 2011-04-03
forum: Networking &amp; Wireless
---

### Post by jacqueshappy on 2011-04-03
Hi there!
I'm very new to Ubuntu and am dual booting it with Vista and I want to be able to access all my files from Vista whilst running Ubuntu. When I go on places, network, and click on windows network, I get a message saying 'Unable to mount location: failed to retrieve share list from server'. 
What am I doing wrong?!

Thanks

---

### Post by wilee-nilee on 2011-04-03
He he, that is not the windows access. First do you have a wubi install or a real partitioned install?

If it is partitioned in that same places dropdown is the windows partition. I think you probably have a wubi though, I forget the access but Ubuntu is just a file in Windows in a wubi; and even when running can get to windows.

---

### Post by bcbc on 2011-04-03
You can access the host windows partition as /host (Places, Computer, File system, host). Or Alt-F2, nautilus /host

see the [wubiguide]("https://wiki.ubuntu.com/WubiGuide") for more info.

---

### Post by jacqueshappy on 2011-04-04
Wow that was magic!
Thanks a million!

---

