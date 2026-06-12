---
title: "launch a server application over ssh"
date: 2013-04-05
forum: Networking &amp; Wireless
---

### Post by thegladfan on 2013-04-05
So i am relatively new to the ubuntu/linux world but not clueless, ive setup a server, installed all the web software, a wiki samba and the like and its working nicely. But im a bit stuck on the graphical and background tasks.The server runs graphical applications like VirtualMachines or grsync but i dont seem to be able to launch the vm or desktop on the machine using ssh. What i want to be able to do is connect over ssh, launch the VM on the gnome gui of the machine that is running and log out. but for some reason it wont let me. When i issue the command to launch via vboxmanage it tries to run in the connected terminal and understandable fails. so the question is how to launch desktop apps using the ssh or how to run VM in the background....

---

### Post by lvlint67 on 2013-04-05
A command similar to vboxheadless should let you run a vm in the background.

The virtual box documentation should cover the matter in detail.

---

