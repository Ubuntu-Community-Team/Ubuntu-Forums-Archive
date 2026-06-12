---
title: "No control center for ATI Catalyst 10.2 update?"
date: 2010-02-28
forum: Multimedia Software
---

### Post by deoanam2002 on 2010-02-28
Hello all,

I'm an Ubunewb, and this is my first post to the forums. Hello!

When I first got my system (Ubuntu 9.10) I had installed the ATI proprietary FGLRX driver for my ATI Radeon HD 4300 card. It worked okay, but there were performance issues so I was happy when the 10.2 catalyst driver update became available.

When I had first installed the proprietary ATI drivers, I also had access to the Catalyst Control Center. When I updated to 10.2, the control center icon disappeared from my menu and seemingly my system. When I go to the "Software Center" to find the catalyst control center and click on it, it reports "Not available in the current data". This is a new behavior as I'm pretty sure it didn't say that before my driver update.

My system is currently completely up to date (so far as the "Update Manager" is concerned).

Has anyone else experienced this problem (with the control center disappearing)?

Thanks in advance!

---

### Post by AKADAP on 2010-02-28
I have 10.2 installed on my system, and the control center is still there.

---

### Post by deoanam2002 on 2010-02-28
Thanks for the reply. I was able to ascertain that people using other distros were able to get the control center, but now I know that it should work for Ubuntu users as well. You're running Ubuntu 9.10? I wonder if there's a conflict with something else on my system... either other drivers or hardware...

> **AKADAP said:**
> I have 10.2 installed on my system, and the control center is still there.

---

### Post by deoanam2002 on 2010-03-01
Interesting. In an unrelated procedure, I followed the steps outlined here:
[http://maketecheasier.com/8-ways-to-maintain-a-clean-lean-ubuntu-machine/2008/10/07](http://maketecheasier.com/8-ways-to-maintain-a-clean-lean-ubuntu-machine/2008/10/07)

When I logged out and logged back in again, Ubuntu said it had to run in low graphics mode. Apparently my system thought that my ATI drivers were not being used and deleted them.

So I reinstalled the drivers, opting for custom install this time and selecting all options. Now it seems that not only is catalyst control center appearing in my Ubuntu control center, but my 3d games are performing way better. So this has been fixed, however accidentally.

---

