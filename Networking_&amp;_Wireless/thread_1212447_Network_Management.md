---
title: "Network Management"
date: 2009-07-13
forum: Networking &amp; Wireless
---

### Post by Arbiter5 on 2009-07-13
I have recently install Ubuntu 9.04, and everything is going smooth. Everything except wireless networking. So I installed ndiswrapper, and all its dependencies so I could use ndisgtk. I installed the driver and the hardware is recognized. But I am still not sure how to connect to the internet. Can anyone help? Someone told me to go to System>Administration>Networking but it wasn't there.

---

### Post by Arbiter5 on 2009-07-13
not even one view...

---

### Post by jualin on 2009-07-13
First we need to know if ndiswrapper is working correctly and which network card do you have. 
Go to the command line and type > sudo ndiswrapper -l and post the output on the forums. What type of wireless card do you have, USB or internal (PCI). 
Also post the output of > lsusb and > lspci This will get you started.

---

### Post by superprash2003 on 2009-07-14
its under system->preferences

---

