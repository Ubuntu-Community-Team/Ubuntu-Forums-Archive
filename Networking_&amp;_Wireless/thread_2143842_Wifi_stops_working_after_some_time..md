---
title: "Wifi stops working after some time."
date: 2013-05-10
forum: Networking &amp; Wireless
---

### Post by Bariseray on 2013-05-10
My wifi stops working after some time and i have to disable and reanble netorking for it to work again and this happens again after some time. I'm completely new to ubuntu so i don't know how to provide any details.

---

### Post by agillator on 2013-05-10
This is a common problem if you are using an adapter that requires the RTL8192CU driver. Some people have been able to fix it, others have not. 
Start by opening a terminal window and entering lsusb if your adapter is an external one that plugs into a usb port, or lspci if it is an internal card or built into the mother board. Look closely at the output and see if you can find your card. If you can, the driver it uses should be shown in brackets. If it is the RTL8192CU, see if this link can help you: [http://ubuntuforums.org/showthread.php?t=2092934&p=12621449#post12621449](http://ubuntuforums.org/showthread.php?t=2092934&p=12621449#post12621449). There is a file there that has solved the problem for some.

---

### Post by Bariseray on 2013-05-10
Mine is RTL8111/8168 should i stil see that link ?

---

### Post by agillator on 2013-05-10
Take a look at it. I'm not sure, but I believe the driver is the same for a range of chips.

---

