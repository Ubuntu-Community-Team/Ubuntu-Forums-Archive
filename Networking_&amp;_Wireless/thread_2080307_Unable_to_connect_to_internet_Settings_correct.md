---
title: "Unable to connect to internet: Settings correct"
date: 2012-11-03
forum: Networking &amp; Wireless
---

### Post by shi89 on 2012-11-03
Hi,
I am unable to connect to the internet on my Ubuntu machine running 12.10.
Same was the case with 11.04.
Internet is fine in the case of Windows 7.
Need urgent help as I want to migrate completely to Ubuntu.

---

### Post by ajgreeny on 2012-11-03
More information please.

Cable, wireless?

Hardware?  Particularly network card if using wireless, so lets see the output of ```
lspci
``` in terminal.

---

### Post by shi89 on 2012-11-09
I am using Wired connection. BSNL modem.

---

### Post by ajgreeny on 2012-11-09
I would still like to see the output of ```
lspci
``` and as the connection is wired, let's also see the output of ```
ifconfig
``` in terminal please.

Finally can you right click on the network icon in your panel, click on Connection information and copy what it says by Default route back here.  It should show something like my screenshot, probably **192.168.#.#** for most if not all routers, the #.# most usually being 0.1 or 1.1, but could be something different.

---

