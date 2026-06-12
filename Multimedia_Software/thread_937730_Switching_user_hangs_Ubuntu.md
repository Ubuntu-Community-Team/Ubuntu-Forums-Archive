---
title: "Switching user hangs Ubuntu"
date: 2008-10-04
forum: Multimedia Software
---

### Post by adm1968 on 2008-10-04
I am using 8.04 with three different boxes, 2 laptops, 1 desktop
I can switch user perfectly with the laptops, but the desktop hangs whenever I try

My wife is an absolute newcomer to Linux, with no personal interest in anything technical, so it is imperative that I find a solution

Have already searched in our forums and the Internet, but I have found nothing practical

(e.g., [http://ubuntuforums.org/showthread.php?t=343507](http://ubuntuforums.org/showthread.php?t=343507))

Anybody else?

---

### Post by adm1968 on 2008-10-06
Forgot to mention:
HP Pavilion Slimline with an ATI Card (proprietary drivers enabled)

Cheers for any help!

---

### Post by adm1968 on 2008-10-19
I think I read something about this being a bug ...
Nobody else?

---

### Post by BFG on 2009-04-09
I just had this.  Fairly new install, getting ready to leave windows altogether and just setting up the other users at home, but it crashes!

Using fast switching results in a prompt for password, enter password and the screen locks.  Restart X does nothing and Ctrl-Alt-F2 doesn't bring up console.

---

### Post by BFG on 2009-04-17
Can't anyone help?  Investigating this on our own means we need to keep powering off, which I never like doing with the discs spinning.

---

### Post by BFG on 2009-04-28
I've just upgraded from 8.10 to 9.04 and user switching now works. :)

):P

---

### Post by Arup on 2009-04-28
In this case its usually compiz which is the culprit, turn off effects in appearance and turn on metacity via gconf-editor.

---

