---
title: "Partial Lock in Frontend"
date: 2010-10-04
forum: Mythbuntu
---

### Post by marduk667 on 2010-10-04
Hi together,

i have installed a new MythTV Box and now i have a problem with some HD-Channels: I can find them with Mythtv-setup but in the frontend/backend i don't get a lock on them.
I can tune in the channels via szap-s2 and ffplay but not in MythTV, any idea how i can solve this? Other HD-channels work fine!

---

### Post by marduk667 on 2010-10-06
and really noone has any idea?

---

### Post by LowSky on 2010-10-06
We need more info.

What tuner, what kind of connection, and have you tried fine tuning the channel from the backend (mythtv-setup)?

---

### Post by bance on 2010-10-06
You'll need to post more on your system info if, someone is to help!

---

### Post by marduk667 on 2010-10-07
Okay, so:

System is a Atom N270 with Nvidia ION chipset.
Tuner is a TT-S2 connect 3600 with s2-liplianin drivers:

> dvb_usb_pctv452e       21281  12 
dvb_usb                19779  1 dvb_usb_pctv452e
dvb_core              102319  2 dvb_usb_pctv452e,dvb_usb
ttpci_eeprom            2167  1 dvb_usb_pctv452e


If i scan the Multiplex from Mythsetup i find the channels and it gets a lock on the multiplex. After saving and leaving Mythsetup i restart the backend and try to watch the channels and here i cannot get a lock on them.

Using szap-s2 on the same channels works and i can watch them via ffplay.

---

