---
title: "Data card"
date: 2013-08-12
forum: Networking &amp; Wireless
---

### Post by Girish_Sharma on 2013-08-12
I have mts MBlaze Ultra ZTE Premium EVDO Modem AC2791. How can I use it ubuntu? Please help asap

---

### Post by varunendra on 2013-08-12
If it is automatically detected by the OS as a "Modem device", the network manager will show a "New Mobile Broadband Connection..." in its drop-down list, clicking on which will start a wizard that will configure the connection for you.

However, if you don't see that option in the NM applet menu, it means your modem may not be natively supported, and then you will need to do some manual tweaking to make it recognised.

If you don't see the "Mobile Broadband" option in the NM applet menu, please unplug --> replug the modem, then run the following commands and show us their outputs -
```
lsusb
dmesg | tail -20
```

---

