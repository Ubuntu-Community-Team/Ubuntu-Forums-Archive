---
title: "network-manager package if only CD access?"
date: 2006-07-02
forum: Networking &amp; Wireless
---

### Post by timrichardson on 2006-07-02
Hear the one about the chicken and the egg?
I have a Ubuntu 6.06 install CD (not the DVD). I have installed it on a machine for which I do not have convenient wired lan access, only wireless. 
It seems that to conveniently configure WPA security, I should use a package called network-manager.
It seems that this package is not installed by default, and that the necessary packages are not on the CD. Or am I missing something? 

thanks for any answers.  

regards,
Tim

---

### Post by reacocard on 2006-07-02
they're not on the CD. just download the .deb files from packages.ubuntu.com (watch out for dependencies) using another computer (or windows, if you still have it), then transfer them to yours and use gdebi or dpkg to install them.

EDIT: I think you also need the wpasupplicant package to get WPA support

---

### Post by timrichardson on 2006-07-03
I, feeling very lazy, downloaded the live DVD: the packages are on it.

---

