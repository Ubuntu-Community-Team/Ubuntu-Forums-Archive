---
title: "No ATI (fglrx) support for below 9500?"
date: 2007-06-05
forum: Multimedia &amp; Video
---

### Post by choksw on 2007-06-05
Hi All, 

I'm a new linux user, recently installed Ubuntu FF on a second hand NEC Versa E6000. I have been experimenting with it and trying to install the fglrx driver by following and comparing several sites from the net. 

I have done the necessary, installing restricted modules, fglrx driver, using aticonfig and editing the xorg.conf (ati string to fglrx and disabling composite)

However my problem is, when I reboot, X doesnt start, and the error was "no screens detected".

To regain access to the GUI,  I reverted to the original backed up xorg.conf file.

After going through other threads in search for help, I come across a comment stating that "fglrx driver does not support ATI cards below the 9500 range" (something along those lines).

I was just wondering, is that statement true? And is that the cause of "no screen detected"? 

The video card on my comp is the ATI Mobility Radeon 9100 IGP.

Please enlighten!

Thanks,
Chok

---

### Post by IanW on 2007-06-05
The statement is true. ATI removed support for the older cards to make room for their shiny new ones.
You'll have better luck with either the "ati" or "radeon" drivers which come built in to Ubuntu.

---

### Post by choksw on 2007-06-05
Thanks! I have since reverted back to mesa. Hope this thread will help users with ATI cards below the 9500 range.

---

