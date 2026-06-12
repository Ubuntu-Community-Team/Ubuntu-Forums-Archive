---
title: "Huawei E600 Help Plseaseee!!!!!"
date: 2005-12-27
forum: Networking &amp; Wireless
---

### Post by erok on 2005-12-27
I'm a bit of a naive in the pcmcia field... so, in short: they offered me a 3G pcmcia card and I just can't make ubuntu recognise it. it shows something related to ohci_hcd but nothing else. anyone knows what's the device? any light? big thanks in advance!

---

### Post by mips on 2005-12-28
Found this [http://lkml.org/lkml/2005/9/22/57](http://lkml.org/lkml/2005/9/22/57)

Looks like support was added in kernel 2.6.14

The Hauwei E600 uses the "Qualcomm 6250 WCDMA" chipset.

I have no experience with PCMCIA cards, hopefully someone else here jumps in. In the meantime have a look at the links below.

[http://pcmcia-cs.sourceforge.net/ftp/doc/PCMCIA-HOWTO.html](http://pcmcia-cs.sourceforge.net/ftp/doc/PCMCIA-HOWTO.html)
[http://tuxmobil.org/index.html](http://tuxmobil.org/index.html)

---

### Post by mips on 2005-12-28
Other cards using that very same chipset are:

Novatel U530
ZTE MF320

from [http://www.qualcomm.com/ir/PDF/pjacobs110705.pdf](http://www.qualcomm.com/ir/PDF/pjacobs110705.pdf)

Do google searches for:
Ubuntu Novatel U530
Debian Novatel U530
Linux Novatel U530
Ubuntu ZTE MF320
.....and so forth.

---

### Post by mips on 2005-12-28
[http://www.java2me.org/news/](http://www.java2me.org/news/)
[http://www.timberwolf.ukfsn.org/debian-orange-3g.html](http://www.timberwolf.ukfsn.org/debian-orange-3g.html)

---

