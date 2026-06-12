---
title: "webcam baptism of fire"
date: 2008-03-15
forum: Multimedia &amp; Video
---

### Post by omar_mandeel on 2008-03-15
Hello,
I recently aquired a webcam, except I havent the faintest idea how to get it to work.  Im guessing I need certain drivers, except I dont know which ones or where to find them. If they dont exist can I just the windows driver + ndiswrapper? Camorama and ekiga both say ¨no video device detected¨. Can anyone help me out or just point me in the right direction? It is an HP 1.3 mega pixel for notebook PCs. The Computer is a Dell, with an Intel Core Do processor running Gutsy. Thanx in advance.

Omar

---

### Post by linuxwizard on 2008-03-15
Post results of the command > lsusb

---

### Post by omar_mandeel on 2008-03-16
Bus 005 Device 004: ID 413c:8103 Dell Computer Corp. Wireless 350 Bluetooth
Bus 005 Device 003: ID 15b8:6001  
Bus 005 Device 002: ID 413c:a005 Dell Computer Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  


I think Device 003 is the webcam. (Thanks again)

---

### Post by linuxwizard on 2008-03-16
I was looking for a ID # & Vendor to figure out which driver you may need. Try using another USB port and than run command again.

---

### Post by omar_mandeel on 2008-03-17
It still gets the same answer just different device

Bus 005 Device 006: ID 15b8:6001  
Bus 005 Device 004: ID 0917:0211 SmartDisk Corp. 
Bus 005 Device 003: ID 413c:8103 Dell Computer Corp. Wireless 350 Bluetooth
Bus 005 Device 002: ID 413c:a005 Dell Computer Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000 

If its any help, its an hp 1.3 megapixel webcam for notebooks (according to the hp website)

---

### Post by linuxwizard on 2008-03-17
The cam is not going to work. Your system is not identifying the webcam. You need a USB vendor ID # & USB product ID # to know what driver you need.

---

