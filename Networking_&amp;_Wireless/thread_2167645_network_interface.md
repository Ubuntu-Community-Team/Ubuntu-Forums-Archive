---
title: "network interface"
date: 2013-08-14
forum: Networking &amp; Wireless
---

### Post by Ram_praveen on 2013-08-14
I an new to ubuntu and i dont know how to install mts mblaze in my system as i have done in any versions of windows.how i can get my ui of my mts connection

---

### Post by SweetAurora on 2013-08-14
I believe that program is Windows only and isn't Linux compatible. So you can't use that. Does the internet still work?

---

### Post by varunendra on 2013-08-15
> **Ram_praveen said:**
> how i can get my ui of my mts connection

You can't unless they have provided a Linux version of their UI program.
However, you don't need that UI if your modem is supported by Linux driver "option" (it is the name of the driver that handles these GSM modems). You can just use the default NetworkManager program in Ubuntu to control and use it.

To determine if your modem is supported or not, please plug-in the modem, run the following command in terminal (ctrl+alt+T) and post back its output here :
```
lsusb
```

---

