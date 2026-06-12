---
title: "need for changing fglrx driver"
date: 2006-07-11
forum: Multimedia &amp; Video
---

### Post by wpshooter on 2006-07-11
I read in another post that installing the fglrx driver (above and beyond this one that is installed when Ubuntu is initially setup) is only necessary for ATI video cards above the Radeon 9200 model.

I have 4 machines, 1 of which has an ATI Radeon 7000, 1 of which has an ATI Radeon 9200, and 2 of which have ATI Radeon 9600s.

Am I correct that I only need to go thru the procedure of installing the new fglrx driver from Synaptic and then editing the xorg.conf file for the 2 ATI 9600 cards but NOT for the 9200 & 7000 ?

Thanks.

---

### Post by operationsone on 2006-07-12
Look up the driver version that the specific target computer has on synaptic, then go to the ati.com website and check if the card is supported (if this information isn't presented in the description of the package in synaptic). If it is supported then you will probably get better speed and results if you install it. If it's not supported then you don't have to do anything.

---

