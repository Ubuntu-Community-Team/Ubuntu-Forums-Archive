---
title: "Radeon X1300"
date: 2007-05-12
forum: Multimedia &amp; Video
---

### Post by RaphaelFaunus on 2007-05-12
Hello. I'm here for help with a particular problem I'm having with my new edition of Linux, Feisty Fawn (Obviously). I'm using Kubuntu, and I got it working well. I downloaded the driver, but I'm having a problem with installing it. The problem here is the following: I'm using x.org Version 7.2, but it wants 7.1, which I don't have.

Here's the thing it gives me:
> root@rfaunus-desktop:~# cd /home/rfaunus
root@rfaunus-desktop:/home/rfaunus# sh '/home/rfaunus/ati-driver-installer-8.36.5-x86.x86_64.run'
Created directory fglrx-install.W24769
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.36.5............................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager
==================================================
Detected configuration:
Architecture: i686 (32-bit)
X Server: X.Org 7.2.x

Detected version of X does not have a matching 'x720' directory
You may override the detected version using the following syntax:
     X_VERSION=<xdir> ./ati-driver-installer-<ver>-<arch>.run [--install]

The following values may be used for <xdir>:
    x430        XFree86 4.3.x
    x430_64a    XFree86 4.3.x 64-bit
    x680        X.Org 6.8.x
    x680_64a    X.Org 6.8.x 64-bit
    x690        X.Org 6.9.x
    x690_64a    X.Org 6.9.x 64-bit
    x700        X.Org 7.0.x
    x700_64a    X.Org 7.0.x 64-bit
    x710        X.Org 7.1.x
    x710_64a    X.Org 7.1.x 64-bit
Removing temporary directory: fglrx-install.W24769

So, anyone have an ideas as to how I'm supposed to install it? I don't really want to downgrade my X Version, because I'm kind of a noob, but I really want this driver.

---

### Post by chrisN_uk on 2007-05-27
Any luck with this?

---

### Post by RaphaelFaunus on 2007-05-27
> **chrisN_uk said:**
> Any luck with this?
I managed to use Envy to run it a bit better, but it still doesn't work as well as it should. Anyone have ANY idea how I can fix this?

---

