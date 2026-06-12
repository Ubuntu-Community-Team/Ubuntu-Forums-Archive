---
title: "Trendnet pcmcia adapter TEW-621PC"
date: 2011-01-16
forum: Networking &amp; Wireless
---

### Post by LaJuan on 2011-01-16
Hi,

I'm running 10.10 on a Dell Inspiron 4150 and I decided to use a TRENDNET wireless N PC card. It worked right out of the box but, I did an update and now it has disabled the wireless network. It doesn't even give me the option to enable the wireless network. Is there something turned off I can turn back on? Very confused...

LaJuan

---

### Post by chili555 on 2011-01-16
I love a mystery. Let's discover why wireless went away and fix it. First, let's see what you have. Please open Applications > Accessories > Terminal and run and post the following with the device inserted.```
lspcmcia -v
uname -r
```Thanks.

---

### Post by LaJuan on 2011-01-17
I see the card status is on. Looks like I need to turn to my network manager and see why the wireless has been disabled. Thanks for the info...

LaJuan:P

---

### Post by LaJuan on 2011-01-20
Solved

---

