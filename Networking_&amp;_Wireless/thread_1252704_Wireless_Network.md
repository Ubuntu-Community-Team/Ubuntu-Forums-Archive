---
title: "Wireless Network"
date: 2009-08-29
forum: Networking &amp; Wireless
---

### Post by karrissaan on 2009-08-29
Ok. I installed Ubuntu Studio, and I have basic experience with general ubuntu, and before, with ubuntu, i didn't need to configure anything for my wireless card. everything was done for me.

Now, I cant get it connected to a network. I really have no clue what to do, and can someone please help me get this card connected to my network.

Regards,

Karrissaan

*edit: I have a D-Link G510*

---

### Post by atomizer on 2009-08-29
We can't help you before we know what chipset is on your D-link adapter.
Please post the output of ```
lspci -C hardware
``` so people can help you further.

---

### Post by karrissaan on 2009-08-29
Sorry about that.

Rev b

RT61

---

### Post by atomizer on 2009-08-31
seems that you have to compile the drivers by yourself, I cannot help you with that.
The source code can be found here:[http://www.ralinktech.com/ralink/Home/Support/Linux.html]("http://www.ralinktech.com/ralink/Home/Support/Linux.html").
You have to google for how to install the drivers, I have no experience with that, or maybe someone else has more experience.

---

