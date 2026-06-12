---
title: "ubuntu 12.04 doesn't detects my capitel connect USB modem"
date: 2013-05-19
forum: Networking &amp; Wireless
---

### Post by dilipv105 on 2013-05-19
hi,

 Am using ubuntu 12.04, i am facing problems while trying to connect the usb modem(capitel connect). it doesn't detected at all and i think it was working well in ubuntu 10.xx versions, plz help.

---

### Post by sanderj on 2013-05-19
Hi, welcome to the forum.


The usual steps:

Open a terminal

Disconnect the usb modem, type "lsusb", connect the modem, type "lsusb", find the new line, post it here, and google it.

And, after connecting the modem, type "dmesg", and inspect (+post) the last 20 lines.

---

### Post by praseodym on 2013-05-19
Please also show the outputs of "lsmod" and "usb-devices"

---

