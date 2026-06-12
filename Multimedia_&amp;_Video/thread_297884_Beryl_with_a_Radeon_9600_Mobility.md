---
title: "Beryl with a Radeon 9600 Mobility"
date: 2006-11-11
forum: Multimedia &amp; Video
---

### Post by brottman on 2006-11-11
To get Beryl working with a Radeon 9600 Mobility should I be using the xorg-driver-fglrx package from the ubuntu repositories or download the fglrx from ati's website?

---

### Post by brottman on 2006-11-12
Bump?

---

### Post by kosmic on 2006-11-12
To use Beryl with xgl you can use the fglrx from the repo's or download from ati site. Both will work.

If you want to use aixgl you can't install the fglrx drivers because the ATI proprietary drivers don't suport some functions necessary for aixgl to work.

---

### Post by brottman on 2006-11-12
So I can't run Beryl on Edgy with a Ati card then? That really sucks.

---

### Post by CarpKing on 2006-11-12
> **brottman said:**
> So I can't run Beryl on Edgy with a Ati card then? That really sucks.

No, you can.  You just have two options for doing so: fglrx + XGL + Beryl, or open source radeon driver (installed by default) + AIGLX (installed by default) + Beryl.  With either you'll need to make sure you have 3d acceleration working first.

---

