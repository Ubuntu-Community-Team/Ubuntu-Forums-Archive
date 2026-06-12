---
title: "Jaunty - VOIP Apps broken or 100% CPU"
date: 2009-05-08
forum: Networking &amp; Wireless
---

### Post by Wellconnected on 2009-05-08
Dear All,
I have upgraded a Xubuntu 8.10 to 9.04.

All my VOIP apps now work badly:
  - Linphone doesn't start
  - Wengophone, Ekiga and Skype all have 100% cpu usage during call, making quality bad and patchy.

Anything I should try to remedy the situation?

Wellconnected

---

### Post by superprash2003 on 2009-05-09
have you installed the latest skype version.. ?

---

### Post by Wellconnected on 2009-05-09
yes.

---

### Post by Wellconnected on 2009-05-14
solution: uninstall pulseaudio

---

### Post by PasQty on 2009-07-06
try that:
[http://www.howtoforge.com/how-to-fix-the-sound-issues-between-skype2.0-and-pulseaudio-on-fedora9](http://www.howtoforge.com/how-to-fix-the-sound-issues-between-skype2.0-and-pulseaudio-on-fedora9)

it is modyfication of pulse config. then you should set for example SBlive (hw:live,0) instead pulse in skype in audio hardware. It works well.

---

