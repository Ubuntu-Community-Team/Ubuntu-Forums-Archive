---
title: "Netgear WNA1000M Wirless USB Adapter Not Functional?"
date: 2013-02-08
forum: Networking &amp; Wireless
---

### Post by 46 and 2 on 2013-02-08
Hello All, 

I am relatively new to Linux and am trying to get my netgear WNA1000M wireless USB adapter to function.  I have tried three different wireless cards to no avail (Netgear WNA 1100, Belkin N150 etc etc).  I have tried just about everything out there that is currently in the ubuntu forums to get my wireless up and running but nothing works.  I know at the end of the day it may be easier to try and get a known compatible adapter that will work out of the box but at this point it is a full fledged mission to get this thing working (and will also help to increase my Linux knowledge).  I am running on Ubuntu 10.04 LTS.  Any help would be most definitely appreciated!!!

Thank You All

---

### Post by chili555 on 2013-02-08
Please run and post:```
lsusb
```Is there any chance you'd install the latest Ubuntu version 12.10? Your device works out of the box, if it's the device I suspect.

---

### Post by 46 and 2 on 2013-02-08
Bus 004 Device 002: ID 046d:c05a Logitech, Inc. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 04f2:1060 Chicony Electronics Co., Ltd 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 0846:9041 NetGear, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


The device is recognized 0846:9041 Netgear, Inc.

Thanks Chili for your help!!!

---

### Post by ahallubuntu on 2013-02-08
~

---

### Post by chili555 on 2013-02-08
It is supported by the driver rtl8192cu; a pain to install in 10.04 and supported well in 12.10. What is your preference? Do you love pain?

[http://wikidevi.com/wiki/Netgear_WNA1000M](http://wikidevi.com/wiki/Netgear_WNA1000M)

---

### Post by ahallubuntu on 2013-02-08
By the way, the "lsusb" is different each time you plug in a different wireless card.  One line of that tells us more about the wireless card.  If you really must use 10.04, one of those cards might be easier than the others to get going.

---

### Post by 46 and 2 on 2013-02-08
Okay I think that may be the best solution, thanks again all.  Only reason I am staying on 10.04 LTS is that my buddy who is a die hard Ubuntu fan swears by it.  I am indifferent as I am still relatively new to the Linux game.  

This may be a stupid question:  But can one just upgrade to 12.04LTS through the update manager, and is the transition to the updated operating system easy or are there additional steps I will have to know about?


Thanks Again

---

### Post by ahallubuntu on 2013-02-08
~

---

### Post by ahallubuntu on 2013-02-08
~

---

### Post by chili555 on 2013-02-08
> unless an updated kernel fixes the problem or something. (I tried only the 12.10 live USB boot.)For those times there is an issue, the backports package usually fixes it.

---

### Post by 46 and 2 on 2013-02-08
Sounds good, I am going to make the upgrade to 12.04LTS.  The machine I am operating on was purchased from a friend so the 10.04LTS is not a relatively new install and there is really nothing saved on the machine so I will just upgrade and start from there.  

Will let you guys know how everything turns out.  Worst case scenario I will post from another one of my machines and let you all know how it turns out. 


Thanks Again

---

### Post by 46 and 2 on 2013-02-08
Thanks Chili55 and ahallubuntu, installed 12.04 LTS plugged in the wireless usb adaptor and zang we are up and running.  I am posting this via wireless connection.  It will take me awhile to get in tune with 12.04 and linux in general but I really appreciate all the help.  

You are Linux masters as many of the workarounds I was trying came from your older posts. 

Thanks again and I am sure you will see me again as I venture further down the "linux rabbit hole"

---

