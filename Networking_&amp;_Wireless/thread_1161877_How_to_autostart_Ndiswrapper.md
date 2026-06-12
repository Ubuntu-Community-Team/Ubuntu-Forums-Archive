---
title: "How to autostart Ndiswrapper?"
date: 2009-05-17
forum: Networking &amp; Wireless
---

### Post by winterg on 2009-05-17
I want to autostart Ndiswrapper. At the moment I'm using a launcher "sudo modprobe ndiswrapper" to get Ndiswrapper working after each reboot.

Executing the launcher gives an errormessage: 
"WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.". 
But works OK after root password has been given.

---

### Post by chili555 on 2009-05-17
The warning is harmless and you may ignore it. I suggest you open a terminal and do:```
sudo gedit /etc/modules
```Add a new item on a new line by itself:```
ndiswrapper
```Proofread, save and close. It should then load on boot.

---

