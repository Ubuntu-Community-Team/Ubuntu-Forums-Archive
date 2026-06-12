---
title: "rfkill says wireless 'Hard blocket'"
date: 2010-05-11
forum: Networking &amp; Wireless
---

### Post by loldrup on 2010-05-11
After a failed suspend attempt (suspend worked fine, but failed to wake up), my wireless card has been deactivated.

loldrup@Jon-Vaio-X:~$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes

The question is: How do unblock it?
Using the rfkill unblock command doesn't have any effect:

loldrup@Jon-Vaio-X:~$ rfkill unblock 0
loldrup@Jon-Vaio-X:~$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes

The computer has a hardware-switch for WIFI, and it is properly switched to ON. Switching it ON/OFF doesn't have any effect.

Computer: Sony Vaio X
Ubuntu: 10.04


Any help is greatly appreciated!

---

### Post by loldrup on 2010-05-11
...and where would be the most appropriate place to bug-report this?

What part of ubuntu is responsible for suspending?
Does it rely on hardware-specific drivers?
Does it depend on specific hardware or 'all of it'?

---

### Post by chili555 on 2010-05-11
You might post it here: [https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.31/+bug/550454](https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.31/+bug/550454)

Or here: [http://permalink.gmane.org/gmane.linux.kernel.wireless.general/48584](http://permalink.gmane.org/gmane.linux.kernel.wireless.general/48584)

---

### Post by loldrup on 2010-05-20
Ubuntu's lack of hardware support for Vaio X is driving  me crazy. I'm dropping it for a macbook air as soon as the updated version is released. Its a pity.

EDIT: Wait a bit - got Eduroam to work. Giving it one more go :)

---

