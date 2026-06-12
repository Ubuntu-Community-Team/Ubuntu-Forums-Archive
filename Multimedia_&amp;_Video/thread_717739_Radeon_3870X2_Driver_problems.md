---
title: "Radeon 3870X2 Driver problems"
date: 2008-03-07
forum: Multimedia &amp; Video
---

### Post by acidPython on 2008-03-07
I've been trying to get this working for a while now, I can't seem to enable hardware acceleration using a 3870X2. I know crossfire doesn't work but won't I be able to use a single 3870 GPU? 

I've tried installing CCC and restricted drivers (using ati linux driver wiki) but am prompted that no driver is needed.

I was wondering if anyone has found a work around for this?

---

### Post by durb on 2008-03-09
I got the card for crysis and ive been tryin to get it working with fglrx too, but no luck so far.  It seems to find both cards but then freakout, so I have been experimenting with the xen kernel and using pciback.hide in grub to try to hide one of the cards.  

Ive got a thread going over here: [http://ubuntuforums.org/showthread.php?t=714560](http://ubuntuforums.org/showthread.php?t=714560)

I was hoping to hide one of the 3870's so fglrx only sees one...

---

### Post by Bateluer on 2008-03-12
Has anyone had any luck with the newer 8.3 drivers? 

I want to get a 3870X2, but I try only to boot into Vista 64 when I want to play certain games.

---

### Post by durb on 2008-03-12
Tried 8.3 and same story, fglrx says no devices detected.  But radeonhd works fine for day to day stuff, obviously with no 3d or 2d accel...

---

### Post by Melcar on 2008-03-12
The card is not supported.  "Technically" the card should work (just one functioning core) but in practice it doesn't.  Only option right now is to use radeonHD (only one core works).

---

### Post by Bateluer on 2008-03-13
How well does it work under the radeonhd driver? Specifically, will I have any troubles running at my 24in LCD's native 1920x1200 res, and will I be able to enable any compiz effects?

---

### Post by Melcar on 2008-03-13
> **Bateluer said:**
> How well does it work under the radeonhd driver? Specifically, will I have any troubles running at my 24in LCD's native 1920x1200 res, and will I be able to enable any compiz effects?


Most likely you won't be able to run Compiz, since the driver still doesn't have 3D acceleration.  You will probably be able to use it for "basic" stuff thought.

---

### Post by durb on 2008-03-13
> **Bateluer said:**
> How well does it work under the radeonhd driver? Specifically, will I have any troubles running at my 24in LCD's native 1920x1200 res, and will I be able to enable any compiz effects?
radeonhd works fine at 1680x1050 (native res on my 22"), right now it only supports the native resolution on a screen so yours should work fine.  And there is no support for compiz yet, because of the lack of 3d acceleration in the driver at this point.

---

### Post by Bateluer on 2008-03-14
I don't suppose anyone knows when ATI's drivers will begin supporting the 3000 series chips?

---

### Post by Melcar on 2008-03-14
> **Bateluer said:**
> I don't suppose anyone knows when ATI's drivers will begin supporting the 3000 series chips?

I know for a fact that HD3850 and HD3870 cards are supported and that the HD3870X2 is not.  Not sure of the HD3650.

---

### Post by Shadowmeph on 2008-03-15
> **Melcar said:**
> I know for a fact that HD3850 and HD3870 cards are supported and that the HD3870X2 is not.  Not sure of the HD3650.

I have the HD single and I can't seem to get the ATI drivers to install at all

---

### Post by Bateluer on 2008-03-15
> **Melcar said:**
> I know for a fact that HD3850 and HD3870 cards are supported and that the HD3870X2 is not.  Not sure of the HD3650.

On ATI's website, selecting Linux as your OS, then Radeon, reveals no 3k series products in the third column. Granted, the 3870 and 2900 aren't exactly dissimilar, but still it does not seem to be officially supported.

---

### Post by Melcar on 2008-03-15
> **Bateluer said:**
> On ATI's website, selecting Linux as your OS, then Radeon, reveals no 3k series products in the third column. Granted, the 3870 and 2900 aren't exactly dissimilar, but still it does not seem to be officially supported.

They still work.  I have a HD3850 on another PC and it's running the latest 8.3s.  Even works better than my HD2900XT (performance wise) for some odd reason.

---

### Post by Bateluer on 2008-03-15
Regardless, I take it no one knows when the Catalysts will officially support the 3000 series.

---

### Post by Melcar on 2008-03-15
> **Bateluer said:**
> Regardless, I take it no one knows when the Catalysts will officially support the 3000 series.

The info just hasn't been updated (don't know why).  The support is there.  It's not beta support if that's your concern.

---

### Post by Nozze on 2008-07-18
> **Bateluer said:**
> I don't suppose anyone knows when ATI's drivers will begin supporting the 3000 series chips?

By the time Ubuntu 8.10 is released AMD will have the drivers for 3870X2 ready.
found information about it here: [http://wiki.x.org/wiki/radeonhd](http://wiki.x.org/wiki/radeonhd)

---

