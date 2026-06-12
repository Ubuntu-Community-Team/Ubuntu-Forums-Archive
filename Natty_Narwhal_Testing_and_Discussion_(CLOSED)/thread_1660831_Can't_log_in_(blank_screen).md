---
title: "Can't log in (blank screen)"
date: 2011-01-05
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by kaldor on 2011-01-05
I reinstalled Natty daily build on Virtualbox. When I log in (I select Ubuntu Classic Desktop) it just hangs. Any fix?

---

### Post by wojox on 2011-01-06
Are you using VirtualBox-4.0?

---

### Post by kaldor on 2011-01-06
Nope; 3.2.8

---

### Post by cariboo on 2011-01-06
Update to vbox 4.0

---

### Post by kaldor on 2011-01-08
Just installed Oracle's Virtualbox 4. Same issue.

---

### Post by jerrylamos on 2011-01-08
> **kaldor said:**
> Just installed Oracle's Virtualbox 4. Same issue.
kaldor, look for the "No Gnome panel" thread.

Jerry

---

### Post by kaldor on 2011-01-09
> **jerrylamos said:**
> kaldor, look for the "No Gnome panel" thread.

Jerry

It's not that there is no GNOME panel; it simply doesn't load. I fixed my missing gnome-panel in a previous install by doing *killall gnome-panel*. This time, it doesn't even get to the login sound.

---

### Post by tokyobadger on 2011-01-09
What's your hardware? What's your host system? Do you have Guest Additions installed? Are you using i386 or amd64? Which version of Natty - alpha1 or a daily build?

---

### Post by kaldor on 2011-01-09
- Virtualbox 4
- LMDE (Debian Squeeze) 32 bit host
- Daily build as stated in my OP

Guest additions NOT installed; it's a fresh daily install.

---

