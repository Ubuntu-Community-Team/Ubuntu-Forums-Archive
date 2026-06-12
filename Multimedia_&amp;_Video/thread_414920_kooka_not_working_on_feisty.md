---
title: "kooka not working on feisty"
date: 2007-04-20
forum: Multimedia &amp; Video
---

### Post by Fenix-TX on 2007-04-20
I open kooka and the application is not shown, if i open process table, i see kooka using 92% (aprox.) of system.

In fact, scanner is not working. I have an EpsonDX500 (multifunctional), in Edgy was working adding id and vendor on /etc/saned.d/epson.conf and on /etc/udev/libsane-extras.rules but in Feisty is not working...



SOLVED


Solved, commenting all the contents on files hplip and libsane-extras from /etc/saned.d/dll.d/

---

