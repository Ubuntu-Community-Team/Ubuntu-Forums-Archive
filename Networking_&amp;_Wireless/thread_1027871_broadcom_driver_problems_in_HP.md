---
title: "broadcom driver problems in HP"
date: 2009-01-01
forum: Networking &amp; Wireless
---

### Post by shanky47 on 2009-01-01
Hello everyone,


I am pretty new to linux and i've installed Intrepid. Now, I'm struck with this wireless problem. I tried going through previous posts, but it only led to more confusion.

I have AMD turion system with broadcom 4318 driver. I switch on the wireless button, but still I dont the wireless option in networking is not active. Its showing as if there are no networks. I understand that there is some problem with driver. I installed ndiswrapper.

I copied the driver folder from windows into desktop and gave the following command,

ndiswrapper -i ~/Desktop/drvinst/b57win32.inf

It says driver b57win32 is already installed.

but ndiswrapper -l says
b57win32: invalid driver.

Did I install wrong driver for windows? I installed the driver I got it with the recovery DVD when I purchased.

So, can someone please tell me wt's wrong with my driver?

Help is highly appreciated!

Thanks,

---

### Post by kevdog on 2009-01-01
Ok
The 4318 chipset is supported by the b43 driver.  Just wondering if you have downloaded the firmware for the b43 driver.  ndiswrapper/windows driver is proabably in my opinion your last viable option, but I would try with the b43 driver first.

---

### Post by acimmarusti on 2009-01-23
Hey there,

I'm also using the same broadcom 4318. I'm using it under ubuntu 8.10 without trouble.

Go here, download the deb package under b43-firmware

[http://ubuntu.cafuego.net/dists/hardy-cafuego/broadcom/](http://ubuntu.cafuego.net/dists/hardy-cafuego/broadcom/)

(I know you are going to say this package is for hardy ubuntu 8.04, but trust me...I've tried the package for intrepid and it doesn't work!)

Once you do that, double click on the package to "execute" it. It will probably ask you for your administrator password. When you are done, restart your computer. Your wireless light should turn on after you log back in ubuntu and you should be able to detect wireless connections close to you.

I hope this works for ya. It has worked for me. If not you are going to have to use ndiswrapper again...

---

