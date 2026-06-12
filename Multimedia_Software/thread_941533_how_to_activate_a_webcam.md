---
title: "how to activate a webcam"
date: 2008-10-08
forum: Multimedia Software
---

### Post by nouraldin on 2008-10-08
hi 
i wrote  in the terminal : 
lsusb
Bus 001 Device 010: ID 0545:8080 Xirlink, Inc. IBM C-It WebCam

and it can see my cam 

then i typed :
sudo apt-get install cheese

but my cam didn't work with cheese why?!
any help 

by the way i am trying to make a security cam is there any other suitable downloads for this :)

thanks for the helpers

---

### Post by nouraldin on 2008-10-09
> **nouraldin said:**
> hi 
i wrote  in the terminal : 
lsusb
Bus 001 Device 010: ID 0545:8080 Xirlink, Inc. IBM C-It WebCam

and it can see my cam 

then i typed :
sudo apt-get install cheese

but my cam didn't work with cheese why?!
any help 

by the way i am trying to make a security cam is there any other suitable downloads for this :)

thanks for the helpers

heeeeeeeelllllllllllllllppppppp

---

### Post by nouraldin on 2008-10-09
I've even tried :

 sudo apt-get install camorama

 but the output :

 cloud not connect to video(/dev/video0).
 please check connection.

but the cam is connected

---

### Post by aidanjt on 2008-10-09
lsusb only shows up what's on the bus, rather than what hardware has been initialised by drivers, check through /var/log/dmesg.  Look for instances of "usbcore" to see what usb driver devices have been initialised by the kernel.

---

