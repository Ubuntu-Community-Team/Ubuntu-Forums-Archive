---
title: "Rosegarden makes the whole system to freeze."
date: 2007-07-12
forum: Multimedia &amp; Video
---

### Post by pitpat789 on 2007-07-12
Hello, I am an absolute noob, and I first experienced Linux just a few days ago.

I installed on my PC Ubuntu 7.04.

I Installed Rosegarden using the "Add/Remove" tool. when I tried to launch it, the system freezed. The mouse didn't work and neither the keyboard and there was no motion on the screen(only one still image).

My sound card is ESI Juli@.

Does anyone know what the problem is?

(sorry for my terrible English)

---

### Post by fredj on 2007-07-12
Rosegarden only works together with the jack audio server. Install jack and qjackctl then use qjackctl
to setup and start jack. Finally start rosegarden.

---

