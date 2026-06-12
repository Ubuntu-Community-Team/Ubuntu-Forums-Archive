---
title: "Fresh installation, no proprietary drivers available"
date: 2013-06-08
forum: Multimedia Software
---

### Post by gigenieks on 2013-06-08
Hello!

Ubuntu 13.04 was installed yesterday. After that I checked some videos / articles "things to do after fresh Ubuntu 13.04 installation". 
I was quite surprised I didn't find any drivers available in Software & Updates >> Additional Drivers for my **ATI Radeon HD 2600 XT**.

How do I find the correct drivers for my graphic card?

---

### Post by deadflowr on 2013-06-08
Support for radeonhd series 2XXX,3XXX,4XXX was dropped by AMD.
And the legacy drivers no longer work with the latest xserver.

This is closest you can get to running the closed source drivers
[https://launchpad.net/~makson96/+archive/fglrx](https://launchpad.net/~makson96/+archive/fglrx)

But it could go either way, it might work or it might not.
I'd rather let the open-source drivers handle it, and not risk the possible serious breakage of trying to downgrade the xserver.

---

### Post by Mark Phelps on 2013-06-08
> **gigenieks said:**
> How do I find the correct drivers for my graphic card?

Unless you're seeing a blank, black screen with no desktop, you already have the correct drivers installed.  The hardware is scanned and the correct video drivers are automatically installed during Ubuntu setup.  Unlike with MS Windows, you don't need to go hunting around for drivers after a fresh install.

---

### Post by Bucky Ball on 2013-06-08
*Thread moved to **Multimedia & Video**.*

Unsure why this was in ***Absolute Beginners***. You have a better chance of getting help posting in the correct category. ;)

---

