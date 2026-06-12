---
title: "Ubuntu 13.04 gets terminated and returns to console window"
date: 2013-08-01
forum: Networking &amp; Wireless
---

### Post by Naveen005 on 2013-08-01
i  installed 13.04......i was using internet by blutooth through  my mobile......while clicking "DISCONNECT" button.....immediatly ubuntu terminated and returned to console window......its displaying like error report... i unable todo anything......i got this error twice...

---

### Post by praseodym on 2013-08-01
Can you hard reset the machine? Please show afterwards the terminel (CTRL+ALT+T) outputs of
```

lsusb | grep Bluetooth 
lspci -nnk
hciconfig --all 
rfkill list
cat /var/lib/NetworkManager/NetworkManager.state 
```

---

