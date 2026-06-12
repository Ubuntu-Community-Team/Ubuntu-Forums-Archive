---
title: "Dell Poweredge 2650 PCI graphics card?"
date: 2009-02-27
forum: Multimedia Software
---

### Post by Dwiman89 on 2009-02-27
Hey, I am trying to put an nvida PCI graphics card in a Dell Poweredge 2650. It doesnt seem to work. the server rack has an on board graphics card thats only 8mb... when I put it in a PCI slot and plug in the monitor and power it up, the monitor doesnt come on... any ideas?

---

### Post by Dwiman89 on 2009-02-28
bumb

---

### Post by overdrank on 2009-02-28
> **Dwiman89 said:**
> Hey, I am trying to put an nvida PCI graphics card in a Dell Poweredge 2650. It doesnt seem to work. the server rack has an on board graphics card thats only 8mb... when I put it in a PCI slot and plug in the monitor and power it up, the monitor doesnt come on... any ideas?

You may have to setup and disable the onboard graphics in bios so that the additional graphics card will work.

---

### Post by Dwiman89 on 2009-03-04
It turns out that the 2650 doesnt support graphics upgrade... SO I traded the computer for a dell sc420. It doesnt work in the ubuntu partition. in the windows partition it will boot all the way up to the windows loader screen, then once its loaded its just a black screen. The very vauge instillation instructions for the e-geforce 6200 says this is because of the onboard grpahics card. There are only two settings in the BIOS for the graphics card( "auto" and "onboard") I have it set to auto, and it still doesnt work.

---

