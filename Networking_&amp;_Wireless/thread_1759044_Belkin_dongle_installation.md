---
title: "Belkin dongle installation"
date: 2011-05-15
forum: Networking &amp; Wireless
---

### Post by johnnie1uk on 2011-05-15
I want to use a Belkin fsd8063 v6  with 10.10 how do i make it work please. full instructions appreciated
thanks in anticipation

John

---

### Post by chili555 on 2011-05-15
I think it's actually Belkin F[COLOR="Red"]5[/COLOR]D8063 v6. Please open a terminal and run and post:```
lsusb
```We'll be in a better position to proceed once we know more details about your dongle.

---

### Post by johnnie1uk on 2011-05-15
Thanks OK this is the result

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 1267:0201 Logic3 / SpectraVideo plc A4Tech SWOP-3 Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 050d:815f Belkin Components F5D8053 N Wireless USB Adapter v6000 [Realtek RTL8192SU]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by chili555 on 2011-05-15
Didn't you plug in the Belkin dongle before you ran the command???

---

### Post by johnnie1uk on 2011-05-15
Yes but the dongle must not have connected properly,it has now,
 so Ive edited it to the correct result

---

### Post by chili555 on 2011-05-15
Which version of Ubuntu are you running? The latest, Natty 11.04 has the driver built in: r8712u. Earlier versions will require downloading the driver from Realtek, compiling and installing; a bit tricky but certainly doable.

---

### Post by johnnie1uk on 2011-05-15
Hi Chilli
im running 10.10 but think i will run the update to 11.04 as its going to make life easier. thanks for your help.

---

### Post by chili555 on 2011-05-15
Post back if we can help you further.

---

### Post by johnnie1uk on 2011-05-15
Upgraded to 11.04 and the wireless dongle connected no problem thanks again.

---

### Post by chili555 on 2011-05-15
Eggs cell ant! Glad it's working.

---

### Post by walt.smith1960 on 2011-05-15
It'll be interesting to see how suspend/resume works.  I had a problem with a different brand Rtl8192SU device and Chili555 came up with the fix.

---

