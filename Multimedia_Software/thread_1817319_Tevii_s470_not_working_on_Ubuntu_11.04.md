---
title: "Tevii s470 not working on Ubuntu 11.04"
date: 2011-08-03
forum: Multimedia Software
---

### Post by roi_shoko on 2011-08-03
Hi,

According to [http://linuxtv.org/wiki/index.php/TeVii_S470](http://linuxtv.org/wiki/index.php/TeVii_S470) 

Tevii s470 DVB card should be supported from kernel 2.6.33.

therefore i installed ubuntu 11.04 but get an error message when trying to scan (dvb-apps).

lspci shows:

03:00.0 Multimedia video controller: Conexant Systems, Inc. CX23885 PCI Video and Audio Decoder (rev 02)”

Running “dmesg | grep dvb” command issues the below:

[    6.034018] cx23885_dvb_register() allocating 1 frontend(s)
[    6.038413] cx23885[0]: cx23885 based dvb card
[    6.178324] cx23885_dvb_register() dvb_register failed err = -1
[    6.178327] cx23885_dev_setup() Failed to register dvb adapters on VID_B

what should i do? 

cheers,

Roi

---

### Post by shternaz on 2011-09-01
Same problem here...!!
can anyone help??

---

