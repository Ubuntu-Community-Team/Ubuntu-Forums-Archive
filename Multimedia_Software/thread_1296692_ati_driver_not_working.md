---
title: "ati driver not working"
date: 2009-10-20
forum: Multimedia Software
---

### Post by htmiimi on 2009-10-20
Trying to use a radeon 4650 card on 9.04 with xorg ati driver, getting

....
ATI Technologies Inc unknown chipset (0x9495) 
......
(II) Primary Device is: PCI 05@00:00:0
(EE) No devices detected.


Does 9.04/ati/4650 work?

Have tried several xorg.confs, fglrx doesn't work either.

---

### Post by edin9 on 2009-10-20
> **htmiimi said:**
> Trying to use a radeon 4650 card on 9.04 with xorg ati driver, getting

....
ATI Technologies Inc unknown chipset (0x9495) 
......
(II) Primary Device is: PCI 05@00:00:0
(EE) No devices detected.


Does 9.04/ati/4650 work?

Have tried several xorg.confs, fglrx doesn't work either.

Which fglrx driver did you try?

---

### Post by htmiimi on 2009-10-20
fglrx: not sure, I used 'hardware drivers' applet at one time, also envyng

Would prefer non proprietary drivers


edit: envy has 8.600-0ubuntu2

---

### Post by edin9 on 2009-10-21
> **htmiimi said:**
> fglrx: not sure, I used 'hardware drivers' applet at one time, also envyng

Would prefer non proprietary drivers


edit: envy has 8.600-0ubuntu2

 If you want any kind of decent 3D acceleration with your 4650 card, you **NEED** to use fglrx. 

You can get a more up to date driver from [here](http://support.amd.com/us/gpudownload/Pages/index.aspx).

---

### Post by htmiimi on 2009-10-21
ok, downloaded that.

I'm not that bothered about 3d though, which is why I wanted the ati drivers.

---

