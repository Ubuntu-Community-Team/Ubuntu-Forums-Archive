---
title: "nexus 4 support?"
date: 2013-08-04
forum: Mobile Technology Discussions (CLOSED)
---

### Post by rms2 on 2013-08-04
im currently considering whether to get a nexus 4 or a jaiyu g3, both look like good phones to me but it seems the nexus 4 is already supported by the ubuntu touch OS, and id really prefer a GNU based phone to an android one. what i want to know is to what extent the phone is supported, is it fully functional as a smartphone(eg, capable of web browsing, camera functions, call and sms functions etc)? is it stable? does it work fine with uk networks?

---

### Post by hansdown on 2013-08-04
Welcome to the forum, rms.

The nexus4 has better documentation.

[https://www.youtube.com/watch?v=TaeUGDMysWc](https://www.youtube.com/watch?v=TaeUGDMysWc)

[https://wiki.ubuntu.com/Touch/Install](https://wiki.ubuntu.com/Touch/Install)

**Please be advised of the inherent dangers of flashing a phone.**

---

### Post by grahammechanical on 2013-08-05
Ubuntu Touch is still under development. Work is still being done on the apps for the phone. So, it is not correct to say that the Nexus 4 is already supported by Ubuntu Touch OS. The Nexus 4 device is one of 4 devices being used by Canonical developers who are making heavy use of existing Android code. So, while the resulting Ubuntu Touch OS will be open source I do not think that it is correct to speak of a Ubuntu phone as a GNU phone.

[http://www.jonobacon.org/2013/06/01/ubuntu-phone-dogfooding-update/](http://www.jonobacon.org/2013/06/01/ubuntu-phone-dogfooding-update/)

[http://www.jonobacon.org/2013/07/05/dogfoodable-core-apps/](http://www.jonobacon.org/2013/07/05/dogfoodable-core-apps/)

---

### Post by Copper Bezel on 2013-08-05
Well, it's a lot simpler to just say that Ubuntu Touch hasn't been released than that it doesn't support the Nexus 4, since it doesn't presently support anything better than it supports the Nexus 4, and it'll presumably support the Nexus 4 as soon as it supports *something*.

As for GNU-ness, I think the only real strike is that Ubuntu Touch excludes X11. (I'm guessing that waiting for a functional Mir to port makes more sense than porting X11 just in time to deprecate it, particularly considering the heavy lifting that's likely to be involved.) While X11 isn't GNU, its absence means that the familiar graphical apps on GNU Linux systems can't be run there, and the core apps are being written for a touch environment in Ubuntu's QML-based SDK. That difference makes Ubuntu Touch substantially less GNU and a little Android-like at a glance, even if the whole GNU toolchain is still available from the command line.

That said, as hwttdz pointed out recently, per [the wiki]("https://wiki.ubuntu.com/Touch/PortingFlippedInProgress#Differences_with_the_Porting_Guide_1.0"),

[QUOTE=The Wiki]For quick reference, these are the current components used from Android:

* Linux Kernel (stock Android kernel provided by the vendor, with a few changes to support some extra features needed by Ubuntu)
* OpenGL ES2.0 HAL and drivers
* Audio/Media HAL and services, to re-use the hardware video decoders
* RILD for modem support
[/QUOTE]

The Android components that Ubuntu *is *using, they'd be a bit daft not to. It's code meant to make the Linux kernel talk to phone hardware (including Google's tweaks to the kernel itself.) Trying to write it from the ground up instead of using Google's freely offered, open source solutions would be pure "Not Invented Here," and half of it is kernel-level stuff anyway, which has nothing to do with GNU taken literally (unless I missed Shuttleworth's decision to switch to Hurd.)

So while it's true that Ubuntu Touch will feel and work less like GNU Linux and more like Android, at least outside of the terminal emulator, that's actually not a reflection of a lack of intrinsic GNU-ness *or* a reflection of the actual Android components used. There's real Android in there, there's real GNU under there (just as much as there is in Ubuntu,) and you can't see either one from the home screen, as it were.

---

