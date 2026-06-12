---
title: "Hauppauge WinTV-HVR1100 DVB-T/Hybrid [card=40,autodetected]"
date: 2008-12-13
forum: Multimedia Software
---

### Post by eanheef08 on 2008-12-13
Hi Here goes my first post so I hope its in the right area.

I am try to get my DVB card to work on ubuntu and not getting very far fast.

I have tried TVTime and MythTV and dont seem to be able to get anything to work.

The following is in /var/log/messages so I presume the OS is seeing the card?

Dec 13 13:45:32 enterprise kernel: [   17.844847] cx88[0]: subsystem: 0070:9402, board: Hauppauge WinTV-HVR1100 DVB-T/Hybrid [card=40,autodetected]
Dec 13 13:45:32 enterprise kernel: [   18.414930] tveeprom 0-0050: TV standards PAL(B/G) PAL(I) SECAM(L/L') PAL(D/D1/K) ATSC/DVB Digital (eeprom 0xf4)
Dec 13 13:45:32 enterprise kernel: [   19.031165] cx88/2: cx2388x dvb driver version 0.0.6 loaded
Dec 13 13:45:32 enterprise kernel: [   19.031172] cx88/2: registering cx8802 driver, type: dvb access: shared
Dec 13 13:45:32 enterprise kernel: [   19.031179] cx88[0]/2: subsystem: 0070:9402, board: Hauppauge WinTV-HVR1100 DVB-T/Hybrid [card=40]
Dec 13 13:45:32 enterprise kernel: [   19.031185] cx88[0]/2: cx2388x based DVB/ATSC card
Dec 13 13:45:32 enterprise kernel: [   19.189891] DVB: registering new adapter (cx88[0])
Dec 13 13:45:32 enterprise kernel: [   19.189900] DVB: registering frontend 0 (Conexant CX22702 DVB-T)...
Dec 13 13:51:13 enterprise kernel: [   18.367198] cx88[0]: subsystem: 0070:9402, board: Hauppauge WinTV-HVR1100 DVB-T/Hybrid [card=40,autodetected]
Dec 13 13:51:13 enterprise kernel: [   19.296248] tveeprom 0-0050: TV standards PAL(B/G) PAL(I) SECAM(L/L') PAL(D/D1/K) ATSC/DVB Digital (eeprom 0xf4)
Dec 13 13:51:13 enterprise kernel: [   19.702286] cx88/2: cx2388x dvb driver version 0.0.6 loaded
Dec 13 13:51:13 enterprise kernel: [   19.702294] cx88/2: registering cx8802 driver, type: dvb access: shared
Dec 13 13:51:13 enterprise kernel: [   19.702302] cx88[0]/2: subsystem: 0070:9402, board: Hauppauge WinTV-HVR1100 DVB-T/Hybrid [card=40]
Dec 13 13:51:13 enterprise kernel: [   19.702309] cx88[0]/2: cx2388x based DVB/ATSC card
Dec 13 13:51:13 enterprise kernel: [   19.883081] DVB: registering new adapter (cx88[0])
Dec 13 13:51:13 enterprise kernel: [   19.883089] DVB: registering frontend 0 (Conexant CX22702 DVB-T)...

Any pointers greatly received...

---

### Post by TheValk on 2008-12-13
I don't know what level Ubuntu you are using but if you have 8.10, then I found that kaffeine supported my Hauppauge Nova-TD straight from install.

Maybe give it a try?

---

### Post by howefield on 2008-12-13
I have this same card also, and it is worked out the box in Ubuntu since 6.06, like the previous poster, I use kaffeine with it.

Sorry I can't give you any pointers other than to confirm it is a great card and will work in Ubuntu.

---

