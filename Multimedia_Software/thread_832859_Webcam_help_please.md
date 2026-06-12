---
title: "Webcam help please"
date: 2008-06-18
forum: Multimedia Software
---

### Post by petronell on 2008-06-18
My laptop has an onboard webcam. When I try to use it Ekira softphone it says the camera is not installed correctly.

Can anyone give me some advice on how to trouble shoot this?

Cheers,

daveR

---

### Post by linuxwizard on 2008-06-18
You may have to work with the settings > Open Ekiga > Edit > Preferences > Video > Video Devices > try changing some of the settings.( Video Plugin if it shows V4L change to V4L2) if working with the settings does not work or help.
Post the results of the command > lsusb

---

### Post by petronell on 2008-06-20
here are the results...

david@barnie:~$ lsusb
Bus 007 Device 003: ID 04f2:b022 Chicony Electronics Co., Ltd 
Bus 007 Device 002: ID 0bc2:0502 Seagate RSS LLC 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

The seagate one is my usb hard disk.

Tried changing the settings as you said and no difference.

Thanks for your help.

daveR

---

### Post by linuxwizard on 2008-06-20
Your webcam > Bus 007 Device 003: ID 04f2:b022 Chicony Electronics Co., Ltd  > listed here as supported > [http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/)  > that is the driver you will need.

---

### Post by marcon00 on 2008-06-20
Sorry for popping in , what if chicony camera fades black if i move ? i need to be still n light needs to be very intense inorder to keep it not fading black .. :S would the driver work maybe ?? happened the same with Vista before, hardware problem ?

---

### Post by petronell on 2008-06-30
Thanks that has worked a treat!

daveR

---

### Post by linuxwizard on 2008-06-30
petronell
You're Welcome Glad that I was able to help you and to hear that you got your webcam working.

---

### Post by rajan dhir on 2008-09-07
hi
i just installed ubuntu 8.04 on a lenovo y300 yesterday 
i'm very new to it and dont know how to install this driver
so can someone please explain how to install step by step to this noob??
thanks a lot

---

### Post by dunbrokin on 2009-03-16
> **linuxwizard said:**
> Your webcam > Bus 007 Device 003: ID 04f2:b022 Chicony Electronics Co., Ltd  > listed here as supported > [http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/)  > that is the driver you will need.

Please can we have more information...what exactly do you download and what do  you do then?

---

