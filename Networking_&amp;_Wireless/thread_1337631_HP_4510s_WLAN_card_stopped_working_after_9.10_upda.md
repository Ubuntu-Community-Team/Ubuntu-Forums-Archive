---
title: "HP 4510s WLAN card stopped working after 9.10 update"
date: 2009-11-25
forum: Networking &amp; Wireless
---

### Post by mudkips on 2009-11-25
Hello!
My WLAN card has always worked well, untill i upgraded to 9.10.
No it says "Cant handle the device".
Can anyone help me please?

//mudkips

---

### Post by pbuddenberg on 2010-01-17
I have the same problem after a fresh install with 9.10 on my 4510s (Celeron).
No sign of wifi anywhere. Not even that it isn't available.
Worked before with previous Ubuntu's.

The network-applet in the right-top of the screen only shows the wired network...

Cannot find much on-line. Did you make any progress so far?

Peter

---

### Post by MarkC502 on 2010-01-17
From what I could quickly google I found you could have this wifi module in your laptops

HP un2400 EV-DO/HSPA

Which Uses The Following Chipset

Qualcomm Gobi

This is a newer chipset and the drivers are not included in 9.10 by default you will need to get them yourself.

Here is a link to the driver you need, you will have to compile and install it though.

[http://www.codon.org.uk/~mjg59/gobi_loader/](http://www.codon.org.uk/~mjg59/gobi_loader/)

Good Luck and welcome to Linux :-)

---

