---
title: "problem with tenda wireless adapter w311n"
date: 2011-06-07
forum: Networking &amp; Wireless
---

### Post by abdoudz on 2011-06-07
[LEFT]hi guys !
i have bought a TENDA adapter w311n.
they writes on its box that it run on linux but it doesn't , I tried to search for a driver on internet but nothing found , 
(I use ubuntu 09.04)
what chould I do ?
thankyou 

[/LEFT]

---

### Post by chili555 on 2011-06-07
> it run on linux but it doesn'tI think it does. We might have to tweak a few things but I think it will run on Linux. Plug it in and open a terminal (Applications > Accessories > Terminal) and run and post:```
lsusb
```Thanks.

---

### Post by abdoudz on 2011-06-07
thanks for the answer , 
i tried to do what you suggested but it still not working 
[http://imageshack.us/photo/my-images/833/screenshotmm.png/](http://imageshack.us/photo/my-images/833/screenshotmm.png/)

---

### Post by chili555 on 2011-06-07
For reference, It's a Ralink 148f:3370.

The command I asked you to run and post was not intended to get your Tenda working; it was intended to gather more information we can use to get it working a few more steps from now.

I think your device is supposed to work, in Ubuntu 9.04, with the module rt2800usb. Let's try it and see what happens:```
sudo modprobe rt2800usb
iwconfig
```I'll look forward to your imageshack.

If we need to, can you get a temporary wired ethernet connection?

---

