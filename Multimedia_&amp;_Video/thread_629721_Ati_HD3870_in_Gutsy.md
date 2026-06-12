---
title: "Ati HD3870 in Gutsy"
date: 2007-12-02
forum: Multimedia &amp; Video
---

### Post by scaven on 2007-12-02
Hi,

I was wondering if anyone has an ATI HD3870 working in Gutsy, or is it not yet supported by the ATI driver?

Cheers,

Scaven

---

### Post by seedofconspiracy on 2007-12-08
I've been having trouble myself.  Gutsy defaults to the generic VESA driver.  I downloaded the ATI-driver-installer-7-11-x86.x86_64.run file from AMD/ATI's website.  The installation went through successfully and installed the fglrx.  Then as suggested at the end of the install, I ran an "aticonfig --initial -f".  After doing so, I restarted X (ctrl+alt+backspace).  The result is a blank/black screen.  It doesn't seem like it's going out of range because my monitor does not go out of sync.  :confused:

---

### Post by ishu on 2007-12-08
experiencing very similar problems with ati hd 2900 xt in 7.10

---

### Post by del_Brujo on 2007-12-09
Same here with a hd 2400 pro agp, black screen after install those drivers.

---

### Post by wintrmute on 2007-12-09
I have a Dell OEM version of the ATI Radeon HD 2400, and have identical problems, using Catalyst 7.11 drivers - X locks the machine up on a blank screen, and/or reboots it. :(

---

### Post by MobiusNZ on 2007-12-11
I just got a new HD3870 after seeing the specs on tomshardware... 4-5fps slower than a $1000 graphics card for $500? Wow :)

I was a bit cautious about ATI as I'd had one before and it was really hard to get going in Linux... not this time though... I downloaded the driver, ran it as root, then aticonfig... then startx all go!

---

