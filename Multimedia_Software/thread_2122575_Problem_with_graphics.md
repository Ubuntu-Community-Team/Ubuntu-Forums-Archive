---
title: "Problem with graphics"
date: 2013-03-05
forum: Multimedia Software
---

### Post by Hexxal on 2013-03-05
Hey ppl i was forced to post since i cant get my ati mobility HD 4570 installed . I am using wubi with ubuntu 12.04.2lts amd 64 version .

---

### Post by QIII on 2013-03-05
*Moved to** Multimedia & Video***

Hello and welcome!

Because ATI stopped Linux driver development and dropped support for HD 2000 to HD 4000 cards, the only way to use those cards with 12.04.2 or greater is with a bit of trickery with downgrading X Server, patching the kernel and using a special legacy driver.

In short, a hodgepodge of changes that I cannot personally recommend because the future consequences are unclear -- what happens when something is updated that upsets that apple cart?  Although there are scripts and methods to do this easily, I don't think it wise.

If you have not done much with your installation, I would recommend installing 12.04 or 12.04.1 instead and using the ATI driver (12.4) available in the Precise repo.  Don't use fglrx-updates because it is most often problematic.  Use the fglrx driver.

Best wishes!

---

### Post by Hexxal on 2013-03-05
Hello thank you for the fast reply :) , ok ty and where i can download previous ubuntu version?

---

### Post by QIII on 2013-03-05
You can download the 12.04.1 version of the wubi.exe [here](http://old-releases.ubuntu.com/releases/12.04/).

I have never used WUBI, so it might be best to start a new thread in the WUBI section to ask for help.

Be sure to have a link back to this thread so that those who can help you will understand why you want to do this.

Best wishes!

---

### Post by Mark Phelps on 2013-03-05
Unlike with Windows, you generally do not go hunting around for drivers in Linux.  If you are getting a desktop, you already have the default Radeon drivers installed.  Unless you need AMD restricted drivers for hardware-accelerated 3D graphics, and/or for GPU temperature control, there really is no reason to try installing the AMD drivers.

---

