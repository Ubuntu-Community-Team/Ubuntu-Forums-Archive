---
title: "Network applet?"
date: 2009-03-10
forum: Networking &amp; Wireless
---

### Post by Prium on 2009-03-10
I accidentally deleted the little applet that normally sits in the upper right corner of the screen that allows one to configure network setting and enable/disable wireless. 

The applets avaialble to 'add to' the menubar don't seem to have the one I am looking for. 

How else can I enable/disable wireless? 

THanks

---

### Post by m_duck on 2009-03-10
It's called "nm-applet" you could run that from the box after pressing alt + f2, or if it has been deleted from the auto start menu you will need to re-add it.

To do this, goto System -> Preferences -> Sessions (or session manager - I can't remember) and look for an entry where the command is (or begins with) "nm-applet". If not, add a new entry with "nm-applet" as the command, log out, then log in and it should be there.

If you have just closed it but not removed it from the autostarted apps, you should be able to log out and in and it should reappear.

---

### Post by Prium on 2009-03-10
thank you - I'll try that tonight

---

