---
title: "AE1200 linksys wireless N adapter won't work on ubuntu studio 11.04"
date: 2011-08-30
forum: Networking &amp; Wireless
---

### Post by stupidtrooper501 on 2011-08-30
i need help the new wireless N adapter [ae1200] i bought will not even show up on my computer running ubuntu studio 11.04. it works on windows [dual boot] but ubuntu doesn't even acknowledged its there. will the adapter only work on windows or is there something i need to do for it to work? please help! i thank anyone in advance that is willing to help. the brand is linksys and it is an external usb wifi adapter the model number is AE1200 the adaptor will not show after using the lsusb command. I am using a dell dimension 3000.

---

### Post by pdc on 2011-08-31
have a wee read 

[http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)

---

### Post by stupidtrooper501 on 2011-09-04
Bus 001 Device 002: ID 13b1:0039 Linksys

---

### Post by Crath on 2011-09-07
I am also trying to get this working on Ubuntu. That thread was not very helpful. Has anyone had any luck?

---

### Post by pdc on 2011-09-07
the post

[http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)

says 

> **Please, provide details about your Wireless**. The diagnoses of your problem can be easer and the solution faster.

.........help others............help you..............

this post

[http://www.wikidevi.com/wiki/Linksys_AE1200](http://www.wikidevi.com/wiki/Linksys_AE1200)

........suggests it may be broadcom............but you can supply some details.......

---

### Post by praseodym on 2011-09-07
If it is a Broadcom chipset, there is only one way to get it work: Find a windows driver and try this one with ndiswrapper. Broadcom USB-devices dont work natively. You may ask Linksys for it.

---

