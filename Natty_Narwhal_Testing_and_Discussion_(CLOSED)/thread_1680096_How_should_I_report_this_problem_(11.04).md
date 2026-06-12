---
title: "How should I report this problem? (11.04)"
date: 2011-02-02
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by sinanaykut on 2011-02-02
Hello. I am not sure if this place is the correct one to ask such a question so please forgive me if I m doing wrong...

I use Ubuntu 11.04 Alpha in daily use and yesterday I've made an upgrade (apt-get dist-upgrade) after restart, I could not access to the desktop. Just the wallpaper and cursor...

I've tried to open it in safe mode, but no luck. Before sending a bug report for this problem, Id like to know some things:

1) Which logs I should consider before sending a bug report? I think this issue is related to updated X.org or Unity desktop files

2) Is there any CLI way to turn my Unity desktop back to the classic one?

Thanks.

---

### Post by Sef on 2011-02-02
Moved to TnD.

---

### Post by vmonkey on 2011-02-02
It is not safe to do apt-get dist-upgrade. I recommend you to just do aptitude safe-upgrade, which avoids you upgrading to such packages.
I personally waited until it was safe to upgrade to the Xserver updates (it seems that you upgraded to them even though their packaging was not complete -> you therefore probably missed some packages and have problems).
To run Natty, I would select in GRUB recovery mode, where would I select to continue in normal system boot (the difference is it starts in text mode - tty1) -> so you login, then if it works run startx just to do sudo aptitude safe-upgrade, but if it does not work (blank screen or so), you should connect internet LAN cable to your PC/notebook to easily do the yet mentioned apt-get safe upgrade etc in the text mode.

---

### Post by Peter09 on 2011-02-02
The problem that you are reporting was common yesterday due to a mis-match of packages. Re-boot and get to a terminal using Cntrl-Alt-F2. Login and update and upgrade. You should end up after a reboot with a working system.

---

