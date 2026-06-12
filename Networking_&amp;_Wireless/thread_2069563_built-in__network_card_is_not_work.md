---
title: "built-in  network card is not work"
date: 2012-10-11
forum: Networking &amp; Wireless
---

### Post by kruvalig on 2012-10-11
Install LUbuntu 12.04.1 on EP-8K9A7I, this motherboard has built-in network card, but in is not work.

ifconfig

  has no eth interfaces.

What can i do to get it work?

---

### Post by albandy on 2012-10-11
Open a console and type:
```

lspci | grep Ethernet

```

and post the result

---

### Post by kruvalig on 2012-10-11
root@ubuntu1:~# lspci | grep Ethernet
root@ubuntu1:~#

My 3G modem work perfectly, but eth do not work.

---

### Post by pqwoerituytrueiwoq on 2012-10-11
output of [FONT=Courier New]lspci[/FONT]
and use code tags
and make sure the onboard chip is enabled in the BIOS and if this has a PCI slot NIC make sure it is seated (plugged in all the way) properly

---

### Post by kruvalig on 2012-10-11
Thank's a lot. I forgot to switch on board chip in BIOS. Sorry, and thank's again.

---

