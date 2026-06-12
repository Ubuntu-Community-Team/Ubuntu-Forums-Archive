---
title: "Beryl causes laptop screen to go blank (white)?"
date: 2007-04-17
forum: Multimedia &amp; Video
---

### Post by hamdodger on 2007-04-17
I am running the latest, patched build of Feisty Fawn 7.04 on a Dell D420 laptop that uses the Intel 945GM chipset, running at native 1280x800 32 bit resolution.  Feisty works great in almost all aspects, except for when I attempt to invoke Beryl, it begins to initialize and then turns the entire screen white.   I can rotate the Beryl cube, and see that it's actually loaded, but nothing on the desktop (not even the menu bars) appear.   The only way to recover is to do a hard power down of the laptop.

Any ideas what would be causing this?

---

### Post by old_geekster on 2007-04-17
Here is a link that might help you with your problem:

[http://ubuntuforums.org/showthread.php?t=272104](http://ubuntuforums.org/showthread.php?t=272104)

---

### Post by Hoopz on 2007-04-23
I have this exact same problem.  Haven't found an answer yet so please let me know and I will do  the same if I figure out what's wrong.

my system AMD64x2 5600+ 2gigs of ram ati x1650pro

here is what it says when I type beryl at terminal and me being a complete noob I don't understand any of it

adam@adam-desktop:~$ beryl
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : XGL

Checking Display localhost:1.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

beryl: GLX_EXT_texture_from_pixmap is missing
beryl: Using non-tfp mode
beryl: GLX_SGIX_fbconfig is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display localhost:1.0

---

### Post by Hoopz on 2007-04-24
I was able to fix my white screen issue by doing a clean install of 32 bit fiesty rather then the 64 bit  I was using.  However beryl isn't running a 100% can't get cube to zoom out before rotating and title bars are missing.

---

