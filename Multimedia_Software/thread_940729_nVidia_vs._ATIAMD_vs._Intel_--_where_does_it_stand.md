---
title: "nVidia vs. ATI/AMD vs. Intel -- where does it stand?"
date: 2008-10-07
forum: Multimedia Software
---

### Post by enigma_0Z on 2008-10-07
I understand that ATI since being acquired by AMD has made great strides in their linux support, and I also hear that there's an opensource ATI/AMD driver that will support the newer cards... I have had a HORRIBLE experience with ATI cards in the past, but this was several years ago using the sucky fglrx driver.

This morning, my nVidia card toasted in my laptop, so I'm going to have to send it back to Dell. I hear that the XPS users are being replaced ATI cards for their old nVidia ones. Worried about this, I have a few questions.

So, my questions are:

1. Can I run compiz on ATI, nVidia, or (newer) Intel cards?
2. How well is ATI's support coming along?
3. What's the deal with ATI's open source driver?
4. What would you recommend?
4a. Is there an Intel card that will keep up with an nVidia GS 8400 (the one that just toasted in my dell laptop)?

Thanks

---

### Post by aidanjt on 2008-10-08
> **enigma_0Z said:**
> 1. Can I run compiz on ATI, nVidia, or (newer) Intel cards?
All three vendors can run compiz via AIGLX (or in nVidia's case, it's internal compositing manager) now, Intel and ATI cards can do so with the opensource drivers, nVidia can only do it with their binary driver.

> **enigma_0Z said:**
> 2. How well is ATI's support coming along?
Brilliantly well, in fact this month saw the demise of the dreaded VT switching (or XServer restart) lockup bug that's plagued fglrx for eons, and support for various X.org features has been growing steadily, AIGLX is natively supported now for e.g., no more Xgl needed to run composite managers like compiz.  On the opensource driver front, practically all GPU chips have at least 2D acceleration support, and 3D & video acceleration support is moving along at a fierce rate wrt R500, R600, and R700 chips, further more, kernel modeswitching support is coming along nicely and we should see that in Ubuntu 9.04, so the entire boot, VT switching, and XServer startup experience should be entirely seamless.

> **enigma_0Z said:**
> 3. What's the deal with ATI's open source driver?
As above, and they're great, easily the most feature complete opensource drivers next to the matrix workstation card support, and intel opensource drivers which are also very good, and being heavy developed by Intel's paid engineers.

> **enigma_0Z said:**
> 4. What would you recommend?
On a budget, Intel are more than adequate if you don't plan on playing any games or use complex 3D rendering software.  Else, stick with ATI, especially on laptops since the entire G80 range of mobility chips are prone to frying themselves.

> **enigma_0Z said:**
> 4a. Is there an Intel card that will keep up with an nVidia GS 8400 (the one that just toasted in my dell laptop)?
Nope, Intel's best GPU is completely pathetic compared to ATI and nVidia's absolute worst.  Even my 7 year old Radeon 9600XT in my P4 computer is faster than Intel's X4500 IGP.  Intel IGPs are designed to only provide rudimentary 3D and HD decode acceleration where power savings is orders of magnitude more critical than horse power (since it's mostly aimed at budget business desktops/laptops), of course Intel is looking to fix this imbalance with it's new Larnabee graphics platform, but no performance figures as of yet, or even basic architecture sketches for that matter.

---

### Post by enigma_0Z on 2008-10-08
> **aidanjt said:**
> Brilliantly well, in fact this month saw the demise of the dreaded VT switching (or XServer restart) lockup bug that's plagued fglrx for eons, and support for various X.org features has been growing steadily, AIGLX is natively supported now for e.g., no more Xgl needed to run composite managers like compiz.  On the opensource driver front, practically all GPU chips have at least 2D acceleration support, and 3D & video acceleration support is moving along at a fierce rate wrt R500, R600, and R700 chips, further more, kernel modeswitching support is coming along nicely and we should see that in Ubuntu 9.04, so the entire boot, VT switching, and XServer startup experience should be entirely seamless.

What would you recommend, if I got an ATI card, the fglrx driver or the opensource one right *now*? I'd of course want compiz and all the effects, but I also need to be able to run a GL app in a composited environment, and multiple monitors and xinerama would be nice too...

> **aidanjt said:**
> ...especially on laptops since the entire G80 range of mobility chips are prone to frying themselves.

Happened to me, heard they were replacing XPS NV chips w/ ATI ones... looking to to some damage control I guess. I'm sending it in soon.

> **aidanjt said:**
> Nope, Intel's best GPU is completely pathetic compared to ATI and nVidia's absolute worst.  Even my 7 year old Radeon 9600XT in my P4 computer is faster than Intel's X4500 IGP.  Intel IGPs are designed to only provide rudimentary 3D and HD decode acceleration where power savings is orders of magnitude more critical than horse power (since it's mostly aimed at budget business desktops/laptops), of course Intel is looking to fix this imbalance with it's new Larnabee graphics platform, but no performance figures as of yet, or even basic architecture sketches for that matter.

Ouch. I hope Intel comes out with a comperable card... I've heard that their Linux support for the driver is the most feature rich... phenomenal in the words of a colleague.

---

### Post by aidanjt on 2008-10-08
> **enigma_0Z said:**
> What would you recommend, if I got an ATI card, the fglrx driver or the opensource one right *now*? I'd of course want compiz and all the effects, but I also need to be able to run a GL app in a composited environment, and multiple monitors and xinerama would be nice too...
It depends on the card, generally speaking, you can expect the opensource radeon driver to be more stable and robust, but newer GPUs are less well supported as far as 3d/video acceleration goes, that'll be the X1000 series up to HD4870 X2.  So for those chips you'll probably want to use fglrx, which for now, are reasonably stable enough, and well featured, so it'll do everything you want it to do.  You might get some video tearing but that's being looked at by AMD, opengl apps will work with a composited window manager but it may demonstrate weird artifacts, although that's a byproduct of AIGLX using DRM1, and will be fixed in DRM2 (which will hopefully be merged into XServer 1.6 (or 1.7) in time for Ubuntu 9.04 (again :)).

Hope that helps clarify matters.

---

### Post by enigma_0Z on 2008-10-08
> **aidanjt said:**
> It depends on the card, generally speaking, you can expect the opensource radeon driver to be more stable and robust, but newer GPUs are less well supported as far as 3d/video acceleration goes, that'll be the X1000 series up to HD4870 X2.  So for those chips you'll probably want to use fglrx, which for now, are reasonably stable enough, and well featured, so it'll do everything you want it to do.  You might get some video tearing but that's being looked at by AMD, opengl apps will work with a composited window manager but it may demonstrate weird artifacts, although that's a byproduct of AIGLX using DRM1, and will be fixed in DRM2 (which will hopefully be merged into XServer 1.6 (or 1.7) in time for Ubuntu 9.04 (again :)).

Hope that helps clarify matters.

Just about... What kind of "artifacts" are you talking about, and is this common across all AIGLX rendering, or just ATI?

Lastly, where can I actually *find* a laptop w/ an ATI card? Do you have a brand recommendation?

---

### Post by aidanjt on 2008-10-08
> **enigma_0Z said:**
> Just about... What kind of "artifacts" are you talking about, and is this common across all AIGLX rendering, or just ATI?
A bit like the old BSP cut bugs you used to find in games, but the tear is blue, but only when you make use of the compositing effects like the cube.  Its common between all drivers using compiz with AIGLX as far as I know, it'll be fixed when DRI2 is pushed out.

> **enigma_0Z said:**
> Lastly, where can I actually *find* a laptop w/ an ATI card? Do you have a brand recommendation?
There's a list of laptop models that use the HD3000 series chips here:
[http://ati.amd.com/products/hd3000partnersproducts.html](http://ati.amd.com/products/hd3000partnersproducts.html)
Use [http://www.froogle.com](http://www.froogle.com) to hunt them down.

Alternatively, you may consider a laptop that uses an nVidia 7000 series GPU, they don't suffer the self-annihilation problems the 8000 series does, and the performance on the 7000 series is very good and no tearing issues.

---

