---
title: "Compiz, fglrx, Radeon 4670, and Karmic (9.10)... it just doesn't work"
date: 2009-10-30
forum: Multimedia Software
---

### Post by NathanA on 2009-10-30
Hi,

I'm using the proprietary ATI/AMD driver supplied with Ubuntu 9.10, and while the driver appears to load fine, I can't get Compiz (or a variety of other GL applications) to run.

I'm running on a Core i5 system, with a Radeon 4670, and the x86_64 distribution of Ubuntu 9.10

Is anyone else seeing this problem, or does anyone have some ideas on how to resolve it?

Thanks.

---

### Post by solnyshok on 2009-10-30
I have Core2 Duo E7300 (overclocked to 3GHz) on Asus P5Q motherboard, HD4670 and everything is fine. Compiz works. 9.10 amd64.

---

### Post by JOHNNYG713 on 2009-10-30
Hi , I run a ATI 9800  in Ultimate Edition (8.10 and 9.04) and I have tried the updated drivers that 9.10 have to no avail ! so what I end up doing is NOT using the proprietary drivers, I just stick with the original drivers installed, and stay away from any driver upgrades, and my compiz works well, how ever my screen will freeze if Atlantis  is running and I deform my desktop for to long, also some screen savers will freeze with compiz running(tentacles,skyrocket and latis) if left to run to long, screensavers wont freeze with metacity as the window manager. ATI drivers are woefully inadequate , and I don't see anything in ATI's future that will change ! it looks like NVIDA is the way to go ! I know in the future I will not buy any ATI products ! as they are not very "LINUX" friendly ! and I don't do windows !

---

### Post by OlorinIWas on 2009-10-30
I can't get jockey to enable ATI/AMD proprietary driver...yes, I've updated sources, and installed the driver myself, and...nothing

---

### Post by NathanA on 2009-10-30
> **solnyshok said:**
> I have Core2 Duo E7300 (overclocked to 3GHz) on Asus P5Q motherboard, HD4670 and everything is fine. Compiz works. 9.10 amd64.Is this with the proprietary drivers?

---

### Post by PorcelainMouse on 2009-11-02
Similar issues with my Radeon HD 4470 (RV740).  Before the upgrade to 9.10, I was running old proprietary drivers I manually installed at least 4 months ago (Catalyst 9.6).  Not learning my lesson from last time, I upgraded w/o backing out to the failsafe X config.  But, to my surprise, it worked fine!  The old 9.6 driver loaded and X seemed to work fine after the upgrade.

Hoping I could get Jockey to install the proprietary drivers from the repository, I purged the packages I manually installed and rebooted.  I had to replace my X11 config with the failsafe one.  But, Jockey (Hardware Drivers) *still* doesn't show drivers for my hardware.

I read some posts about Karmic beta suggesting that it was the new unsupported kernel, 2.6.31, but that was the same excuse for 2.6.28.  Did the kernel break fglrx again?  I don't think so.  Why doesn't the RV740 chipset get recognized by Jockey?

---

### Post by fooey on 2009-11-02
sigh. no fglrx support for Radeon 2400 XT :cry:
back to 8.04 i guess..

---

### Post by M20554443 on 2009-11-05
Same for me: Radeon HD 4670 and fglrx in Karmic isn't working.

---

### Post by Contemplator on 2010-01-11
> **NathanA said:**
> Is this with the proprietary drivers?

Proprietary drivers are drivers NOT included in the Ubuntu repositories. This DOES include drivers from amd.com (The manufacturer).

What I'm wondering is, what version of linux AMD are using to test their drivers. I'm also wondering, why it's working for some people and not others. A third thought is, if AMD drivers are indeed proprietary, where the repository drivers emerge from and why it gives a different result.

---

### Post by markbuntu on 2010-01-11
The fglrx driver available from jockey is a beta of the 9.10 driver that was packaged by the Ubuntu maintainers and ati so it could make it into the Karmic release. 

If this driver does not work for you you should remove it and any other old drivers and fglrx kernel modules left over from upgrades etc and get the latest 9.12 driver from the ati site.

These are basically the things that will cause the driver to fail. 

1. Old drivers and their kernel modules are not removed before installing the driver
2. The driver you does not fully support the card because your card was released after the driver. This can happen with many 46xx and 47xx and mobility 3xxx cards and some 3xxx and 4xxx igps and the 5xxx cards.
3. After initial system install the driver was activated/installed before getting updates. It is very important to get all the latest updates before atteptimg to install the driver.
4. An nvidia or other proprietary driver was not removed completely before installing the ati driver
5. A 2.6.32 kernel is in use
6. the command aticonfig --initial was not implemented after driver install.

---

