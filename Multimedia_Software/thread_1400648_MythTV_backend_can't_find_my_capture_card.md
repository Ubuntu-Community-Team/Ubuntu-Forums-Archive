---
title: "MythTV backend can't find my capture card"
date: 2010-02-07
forum: Multimedia Software
---

### Post by JeyPeyy on 2010-02-07
I'm trying to setup Mythbuntu on a computer connected to a TV. I have bought an USB DVB-T Receiver, named WandTV. [According to LinuxTV]("http://www.linuxtv.org/wiki/index.php/DVB-T_USB_Devices#DVB-T_USB_Devices"); WandTV, aka Shenzhen Forward Video EzTV859, is supported in the Linux kernel. 

When I try to setup the mythTV backend I'm being asked of what card type I have. I guess the answer to that is "DVB DTV capture card (v3.x)", but no matter what I choose, it can't find any devices. 

I'm pretty sure /dev/hidraw0 is the receiver, can I use that to setup the backend?

---

### Post by JeyPeyy on 2010-02-07
Anyone?

---

### Post by JeyPeyy on 2010-02-07
Being supported in the kernel means that there are no drivers to install, right?

---

### Post by Red Kelly on 2010-02-20
I'm in the same situation. I had to get drivers from System>Admin>hardware drivers. This all seemed to work but MythTV can't find the capture card.

---

