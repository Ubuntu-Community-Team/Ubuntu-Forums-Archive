---
title: "Wi fi not working with Dell 1440 Laptop"
date: 2009-12-10
forum: Networking &amp; Wireless
---

### Post by Aneesh John on 2009-12-10
I am using Dell inspiron 1440 Laptop. After installing Ubuntu 9.10 my lap top is not showing any wi fi internet connections. Please help me in getting connected to wi fi internet connections.

---

### Post by shredder12 on 2009-12-10
Assuming that you have already checked the wireless switch. (it sounds stupid but this happens) .. check if you have the driver installed..

Go to System->Administration->hardware drivers and see if you see any option for wireless driver..

---

### Post by Aneesh John on 2009-12-13
Thank you for your reply. Please note that broadcom wireless B43 driver is activated in my system.

---

### Post by shredder12 on 2009-12-20
If you still having trouble then right click on the Network manager tray icon and see if the enable wireless is checked..
and when you are around a wireless network (you are sure that it exists) then post the output of 
```
sudo iwlist eth2 scanning
```
replace eth2 with your wireless interface

---

