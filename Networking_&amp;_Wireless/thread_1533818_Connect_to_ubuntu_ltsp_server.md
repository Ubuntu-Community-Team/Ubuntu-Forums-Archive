---
title: "Connect to ubuntu ltsp server?"
date: 2010-07-18
forum: Networking &amp; Wireless
---

### Post by pythonscript on 2010-07-18
I installed an ubuntu ltsp server, and it properly configured the static IP for it and all of that, but I'm wondering how I can connect a thin client to it? All the information I could find said it applied to Ubuntu <= 6.06, and since I'm using 10.04 I didn't want to risk trying it. 

Is there a way to just boot an empty system off the network and use the server that way (just using the apps/system over the LAN) or do I need to install an ubuntu thin client on the empty computer too?

---

### Post by david10 on 2010-07-20
The way I am trying out LTSP is by using 2 computers running Virtualbox - 1 for the server and 1  for the terminals

---

### Post by pythonscript on 2010-07-20
That's how I've decided to try it too; do you have any more information on how to set this up, though? ...

---

### Post by david10 on 2010-07-20
I've had success with Alternate 9.10. In a new Ubuntu machine in VirtualBox

Disconnected from DHCP router, use 2 network cards bridged - setting a static reserved address router address  for eth0.

Built clients booting from network on the other machine with no hard drive, reconnected home network. Works and worked for a school client machine when tested.


With Alternate Install 10.04 and Edubuntu 10.04 booting a client  I can only get to the same spot on each 

pxe 
vmlinux
initrd.img..........................ready then nothing where before the ubuntu loaded.

---

