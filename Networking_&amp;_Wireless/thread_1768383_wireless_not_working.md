---
title: "wireless not working"
date: 2011-05-26
forum: Networking &amp; Wireless
---

### Post by Fordz on 2011-05-26
My Ubuntu when i start it up, go to the wireless networks , try to connect to my network it trys to connect stops than says disconnected. My internet card is a Cisco Aironet wireless (idk the model number) Can anyone help?

---

### Post by josephmills on 2011-05-26
hi there could you please open your terminal (ctrl+alt+t)and type in  ```
lspci -nn
``` and if this is a usb wifi thingy then ```
lsusb
``` and a ```
rfkill list all 
``` and paste that all here thanks

---

