---
title: "AMD64 + ndiswrapper"
date: 2006-01-11
forum: Networking &amp; Wireless
---

### Post by GQed76 on 2006-01-11
Ok on my i386 install I finally got my netgear311 to work.  Disabled the system from installing the acx_pci by blackisting it and using ndiswrapper to use the latest window driver.

I decided to try AMD64 on another partition. (my grubs a mess!)
I found 1.1.4 of NDIS wrapper for amd64 installed it.  Installed the same drivier i used for the i386..no dice.
Used several drivers even an alleged 64 bit driver (not from netgear) and that didnt work either.

Now i see NDISwrapper is at 1.7,but cant see a 64 version.  Are they universal, or is 64 bit support stopped.  Should i force the install?

Even if i do get ndiswrappers latest version installed...do 32 bit drivers even work?  Netgear has proudly announced they arnt doing any support for 64 bit drivers.  Not suprising considering their products are basically crap wraped in a box...but I digress..

---

### Post by Dr. Nick on 2006-01-11
I had the same expierence with my linksys on my 64bit ubuntu, Ndis wrapper is made for 64bit but my drivers were 32 and it gave me an error telling me basically that you cant use 32bit drivers on 64bit. 

Whats wrong with acx_pci driver?  I havent used it, but I had to stop my native driver since it was annoying to configure (prism2)

---

### Post by GQed76 on 2006-01-11
just doesnt work on my system 32 or 64 bit

---

### Post by Dr. Nick on 2006-01-11
If you need the wireless card and the native drivers do not work, meaning you need ndiswrapper then I think installing the 32bit version of ubuntu on on your 64bit processor is the only way it could work then. I dont know of any way to get the 64bit ndiswrapper to use a 32bit driver. :(

---

### Post by GQed76 on 2006-01-11
damned netgear.  time to go look at D-link

---

### Post by bato on 2006-03-07
You have to downloaded the 64 bit driver for windows and use ndiswrapper with that. For me it works.

---

