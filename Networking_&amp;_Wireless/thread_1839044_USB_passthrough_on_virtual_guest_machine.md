---
title: "USB passthrough on virtual guest machine"
date: 2011-09-04
forum: Networking &amp; Wireless
---

### Post by ether3al on 2011-09-04
Hi All,

I have recently installed Ubuntu 11.04 on a Virtual Box guest host. I am trying to get a Ubiquiti SR71USB(Ath9k driver) working. This card works out of the box when using it with a dedicated install of Ubuntu however when using a virtualized host the interface never becomes available. 

The drivers are clearly loaded when i issue an "lsmod & lsusb". 

Thanks in advance.

---

### Post by haqking on 2011-09-04
> **ether3al said:**
> Hi All,

I have recently installed Ubuntu 11.04 on a Virtual Box guest host. I am trying to get a Ubiquiti SR71USB(Ath9k driver) working. This card works out of the box when using it with a dedicated install of Ubuntu however when using a virtualized host the interface never becomes available. 

The drivers are clearly loaded when i issue an "lsmod & lsusb". 

Thanks in advance.

are you a member of the vboxusers group ?

in terminal type the following

[I]sudo usermod -a -G vboxusers username             

[/I]where username is your username obviously

also good idea to add the virtual box extensions pack from [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

---

### Post by papibe on 2011-09-04
How did you get the VirtualBox software for the host machine?
If the host is Ubuntu, Did you get it from the Software Center?

Regards.

---

