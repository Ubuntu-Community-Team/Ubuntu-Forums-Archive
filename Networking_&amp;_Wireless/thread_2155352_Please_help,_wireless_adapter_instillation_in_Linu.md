---
title: "Please help, wireless adapter instillation in Linux"
date: 2013-06-18
forum: Networking &amp; Wireless
---

### Post by bluedot33 on 2013-06-18
I am a newbi to Linux and I really love its flexability; however I have  an HP Dv9205US but the wireless is not workng. I am using a Netgear  wireless USB adapter and it works great; however it sticks out awfully  far. I ordered an Airlink Wireless N USB adapter but found out tha it  wasn't compatable with Linux. I then ordered a Monoprice USB wireless adapter  which is supposed to be compatible with Linux but I can't install it.  Linux does not seem to be plug and play when it comes to these devices and the disk that came with the device has several files and folders  that I don't know what to do with.

Could someone please help me

---

### Post by praseodym on 2013-06-18
Hi,

please open a terminal with CTRL+ALT+T and show the output of the command:
```

lsusb
```
after plugging either stick. Does LAN work? Is it 32 or 64bit?

---

