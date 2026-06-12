---
title: "Hardy ATI Legacy cards with &quot;big font&quot;"
date: 2008-04-23
forum: Multimedia Software
---

### Post by sulligogs on 2008-04-23
Installed Xubuntu 8.04 Beta (not sure which version of the beta) and just like the final release of Xubuntu 7.10 I get a "big font" on the login screen. I have a PCI legacy ATI Radeon 9250 graphics card.


 I managed to find a fix for the "big font" problem by editing xorg.conf and inserting these lines into the section "Device" :-


 Option    "UseEdidDpi"    "FALSE"
Option    "DPI"                "96x96"
Option    "NoDDC"
 

This also fixed the same "big font" problem on the beta of Xubuntu 8.04. Just thought I would add my two cents for what it's worth.  I have filed a bug report on it anyhow.  Maybe newbies won't be scared off by seeing such a disfigured login screen.

---

