---
title: "Wifi Adapter Working But Not Connecting"
date: 2013-02-10
forum: Networking &amp; Wireless
---

### Post by marsdend on 2013-02-10
Hi guys,

Ive recently purchased a HP Pavilion G6 2241sa and installed Ubuntu 12.10 64bit.

Everything is working perfectly! The only problem I have is that the wifi doesnt want to connect, the card is working and its picking up all the routers but when i click connect and enter my code it tries for a while and then says "Wireless network - Disconnected"

I dont know where to start with this, any help would be greatly appreciated.

Kind Regards,
Dan

---

### Post by praseodym on 2013-02-10
Hi,

please show
```

lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
sudo iwlist scan
iwlist chan
```
Do you have a wired connection available? Check, if you are using pure WPA2-AES encryption.

---

