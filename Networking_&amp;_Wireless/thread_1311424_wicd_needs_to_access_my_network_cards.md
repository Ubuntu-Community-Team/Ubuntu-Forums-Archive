---
title: "wicd needs to access my network cards"
date: 2009-11-02
forum: Networking &amp; Wireless
---

### Post by castor_fou on 2009-11-02
since upgrading to koala, during boot process I am presented a basic xwindow, asking a password (I guess) with a message : wicd needs to access your network cards.
I can enter the password or just click cancel, I then enter gnome and wicd connects to wifi. (yes even if i cancelled)
anyone with the same issue ?

should try with a fresh user (not one coming from 9.04)

---

### Post by jkarcz on 2009-11-02
Sometimes, a "[ ]" (open and close square brackets) are present on line by itself in the wicd conf file.

I believe the file is: /etc/wicd/wired-settings.conf

Just removing the "[ ]" and logout and login should help.

---

### Post by castor_fou on 2009-11-02
answer to myself.
I went on System > Login screen and checked : Show the screen for choosing who logged in. Reboot, it worked.
Switched back to Log in as <self>. Reboot, it now works.
Don't know what happened

---

### Post by ziphyre on 2011-03-14
> **jkarcz said:**
> Sometimes, a "[ ]" (open and close square brackets) are present on line by itself in the wicd conf file.

I believe the file is: /etc/wicd/wired-settings.conf

Just removing the "[ ]" and logout and login should help.

Thanks, that solved my problem.

---

