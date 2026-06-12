---
title: "A question about the &quot;depreciated&quot; status of ati cards post cat9.3"
date: 2009-05-03
forum: Multimedia Software
---

### Post by molochi on 2009-05-03
Recently AMD dropped support for a large chunk of its video card history. Meaning radeon 9500 - X19yy (plus some low end X2yyy cards) series users must either stick with the catalyst9.03 derived proprietary drivers under Ubuntu 8.10 Ibex or switch to the open source radeon drivers under 9.04 Jaunty. At least that's how I understand it. As a side note this change affects a huge install base ranging from older desktops with Pentium4 and AthlonXP CPUs that are still plenty useful in Ubuntu, to fairly recent Core and Athlon 64 X2 systems that are stuck with an AGP videocard, to more recent laptops that may only be a couple of years old.

1) Does anyone know if the open source driver team has received (or has been promised) anything from AMD to allow them to support all these cards?

2) Does the open source driver succeed in supporting 3D and Compiz on older cards like the radeon 9200?

2) Is there an easy or at least documented way to install Ubuntu 9.04 with the older fglrx drivers as a target?

---

### Post by markbuntu on 2009-05-04
ATI has given the open source drivers all the information they can and provided people and money to the effort. The cards dropped from the proprietary driver have 3D support in the latest ati and radeon and radenhd open source drivers which are vastly improved from ones included in previous Ubuntus and are rapidly improving further.

You would need to downgrade the X to a previous version to use the 9.3 or older driver and I am not sure that you could do that successfully.

Don't feel so bad, ati has dropped those cards from it windows drivers as well and there is no open source alternative for that.

---

### Post by usergentoo on 2009-05-04
I downgraded xorg to use the older ati drivers just have a few minor issues to work thru in Jaunty.

---

