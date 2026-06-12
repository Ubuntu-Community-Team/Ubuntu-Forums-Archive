---
title: "Please help connecting to wireless network with a Realtek card!"
date: 2010-09-21
forum: Networking &amp; Wireless
---

### Post by raptura on 2010-09-21
Sorry if this has been posted before, but I have searched the internet to no avail.  I am trying to have my computer connect to the wireless network with Ubuntu 10.04.

Also, no drivers show up in System > Administration > Hardware Drivers.

From my searches, I believe this should help.

```
lspci | grep "Network"
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8172 (rev 10)
```

Edit: if it helps, my laptop is a Toshiba Satellite a505-s6005.

---

### Post by dineshs on 2010-09-21
See if #11 [here]("http://ubuntuforums.org/showthread.php?t=1470732") can help

---

### Post by raptura on 2010-09-21
I was trying that yesterday. Though I am a bit of a Linux noob, after a while I noticed that the kernel seems to have already been updated by the Ubuntu developers, I am not sure where to begin if that is the case.

---

### Post by raptura on 2010-09-21
Please, help. Any assistance is appreciated.

---

### Post by Ben_neB on 2010-09-22
are you sure the hardware is even working? If so, what happens when you try to connect? Does it see the wireless networks?

---

### Post by raptura on 2010-09-22
No, it doesn't see the network when I choose the "connect to hidden wireless network" option.

---

### Post by Ben_neB on 2010-09-22
Stupid question here, but is there a button or switch on the laptop to enable the wireless card?

---

### Post by raptura on 2010-09-22
Well, yes there is, but right now, I have it switched and an LED light is turned on. I assume this means that the wireless card is not cutoff.

Oh, yeah, and the wireless does work on my windows partition, just in case anyone asks.

---

### Post by raptura on 2010-09-23
Okay, it is just like post #2 said. Check out his link. I also posted an update on that thread (see page 6) as of September 22, 2010 on that method. It really does solve a LOT of problems for my fellow toshiba users.

---

