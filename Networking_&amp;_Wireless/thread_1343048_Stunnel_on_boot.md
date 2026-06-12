---
title: "Stunnel on boot"
date: 2009-12-01
forum: Networking &amp; Wireless
---

### Post by new_tolinux on 2009-12-01
I have installed stunnel4 and enabled it in both /etc/init.d/stunnel4 and /etc/default/stunnel4
As my (virtual) system boots, it loads perfectly, but it seems tty1 is locked out for use.
I can only use tty2 and on, where I can use the connection configured in stunnel

Did I do anything wrong?
I have installed 9.04 (alternate) text-only (so no gnome/kde).

---

### Post by new_tolinux on 2009-12-06
A little update.
Not everything is working, the apache2-service does not start on boot either.
My guess is that the complete boot-sequence stops while loading stunnel

tty2 is still working, and I can start apache2 manually (/etc/init.d/apache2 start).
Tried to get the latest updates (apt-get update & apt-get upgrade) but still no luck.
Any ideas?

---

### Post by new_tolinux on 2010-06-03
As I decided to remove the only job that used this tunnel after installing 9.10, I won't put any more effort in solving this problem. Therefore I'll marked it as solved.

---

