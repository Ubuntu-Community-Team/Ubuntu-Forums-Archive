---
title: "regarding the need for graphics hardware driver"
date: 2009-11-09
forum: Multimedia Software
---

### Post by cnbiz850 on 2009-11-09
I am somewhat confused about whether I need to install the restricted graphics hardware driver.  Without it, my screen display if alright, and the 3D graphics like Google-Earth works fine.  It seems adding it is just for screen visual effect (compiz).  Is that right?  I would think that it should help out graphics displays, but I can't verify in anyway.  

Anyone please help clarify?

---

### Post by ssam on 2009-11-10
depends on which graphics card you have. ubuntu by default installs only opensource drivers.
intel: there is only an opensource driver, it does 3d fine
nivida: opensource driver only does 2d, need restricted/proprietary for 3d
ati: opensource driver does 2d, and 3d on most cards (getting better fast), need restricted/proprietary for 3d on new cards.

if google earth works, then compiz should.

---

