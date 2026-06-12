---
title: "Via gigabit network adaptor"
date: 2012-07-14
forum: Networking &amp; Wireless
---

### Post by rakuba on 2012-07-14
I am running 12.04 on a Sony Vaio VGN-SR41M, have just got an expresscard gigabit adaptor:
03:00.0 Ethernet controller: VIA Technologies, Inc. VT6120/VT6121/VT6122 Gigabit Ethernet Adapter (rev 82)
as soon as I plug a network cable into it the whole system freezes up.
Is there some magical incantation I can use to get it going, or is there a compatibility list I can check it against.
Thanks in advance for any suggestions

---

### Post by Kirk Schnable on 2012-07-15
It looks like it should be supported with the vge driver. See here: [http://manpages.ubuntu.com/manpages/precise/man4/vge.4freebsd.html](http://manpages.ubuntu.com/manpages/precise/man4/vge.4freebsd.html)

Kirk

---

### Post by rakuba on 2012-07-15
> **Kirk Schnable said:**
> It looks like it should be supported with the vge driver. See here: [http://manpages.ubuntu.com/manpages/precise/man4/vge.4freebsd.html](http://manpages.ubuntu.com/manpages/precise/man4/vge.4freebsd.html)

Kirk

Thanks Kirk, I will check that out

---

