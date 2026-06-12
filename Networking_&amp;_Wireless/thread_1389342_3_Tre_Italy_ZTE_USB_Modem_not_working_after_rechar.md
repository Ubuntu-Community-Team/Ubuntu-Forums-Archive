---
title: "3 Tre Italy ZTE USB Modem not working after recharge"
date: 2010-01-24
forum: Networking &amp; Wireless
---

### Post by eggnogg on 2010-01-24
Hello,

I have a ZTE USM Modem from 3 Tre Italy, on the tre.it network.

The modem worked fine for a month or so. Yesterday I recharged the SIM and the modem has stopped working after midnight.

Earlier, the modem would indicate a red light, and then turn to green, blink a few times, and connect on its own.

Now, it shows red, goes off, and then stays red constantly.

I've tried putting the priginal PIN that came with the SIM into my Mobile Broadband settings in Network Manager to no avail.

Can anyone help me? I run Karmic.

Here is my lsusb:

Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 051: ID 19d2:0064 ONDA Communication S.p.A. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


Please help!

---

### Post by eggnogg on 2010-01-24
No one? Please help!

---

### Post by pdc on 2010-01-24
1) what do you mean by 

> *Yesterday I recharged the SIM *and the modem has stopped working after midnight.


2)in a terminal type

> ls /dev/ttyUSB*

if you get any positive answers, type

> screen /dev/ttyUSB2

when you get asked for a prompt, type

> ATI

copy and paste the results back here;

(It must be the middle of the night in Italy?)

---

### Post by eggnogg on 2010-01-25
Hi, here is the output:

Manufacturer: ZTE INCORPORATED
Model: MF627
Revision: BD_3GHAP673A4V1.0.0B05
IMEI: 358066025200766
+GCAP: +CGSM,+DS,+ES

OK

---

### Post by pdc on 2010-01-25
1) what do you mean by

Quote:
Yesterday I recharged the SIM and the modem has stopped working after midnight.

---

### Post by eggnogg on 2010-01-26
By this I mean that I recharged my SIM card (it is a Tre Ricaricabile account, that translates as 'rechargeable account')

After the recharge, the modem worked fine till midnight. 
I suspect around midnight something kicked in and I needed to enter a new pin or something. 

Such a screen does not show up in Linux. I remember having seen such a screen on a Mac, and I plugged the modem into a Mac. 

However, Macintosh now detects the modem only for a few seconds and the device disappears from Finder. 

That is what I meant.

---

