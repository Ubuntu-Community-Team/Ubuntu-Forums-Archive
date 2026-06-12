---
title: "ATi driver issues after AMD K7 SMP update"
date: 2006-06-29
forum: Multimedia &amp; Video
---

### Post by Jason9875 on 2006-06-29
Well I updated to get SMP support (gotta love dual core!) and after reconifguring xorg, I boot up and to test the drivers I did "fglrxinfo" to see if the drivers were working properly, and well they aren't.

So I tried uninstalling/reinstalling them and I still can't seem to get the ATi drivers to work.

Any ideas (Im also a complete noob so don't leave out the obvious =P)

---

### Post by whatever on 2006-06-29
you might need to recompile the fglrx kernel module

---

### Post by Jason9875 on 2006-06-29
Ok I have tried to recompile it.

But when I do "sudo module-assistant build,install fglrx" it replies with
"fglrx, what is fglrx?"

well after having reinstall the drivers, and seemingly didn't recompile them, I rebooted and the drivers are working fine.

---

