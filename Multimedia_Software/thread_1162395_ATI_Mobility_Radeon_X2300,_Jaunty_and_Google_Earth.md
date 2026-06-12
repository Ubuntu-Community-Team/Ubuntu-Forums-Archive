---
title: "ATI Mobility Radeon X2300, Jaunty and Google Earth"
date: 2009-05-17
forum: Multimedia Software
---

### Post by haba7 on 2009-05-17
After upgrading to Jaunty, Google Earth became extremely slow; ATI Catalyst 9.3 does not support the new X.Org version and ATI Catalyst 9.4 [does not support]("http://ati.cchtml.com/show_bug.cgi?id=1556#c1") ATI X-series graphics cards... even though my [Mobility Radeon X2300 is not that old]("http://en.wikipedia.org/wiki/Comparison_of_ATI_graphics_processing_units#Mobility_Radeon_Series").

So, which driver I should choose to get my Goole Earth work again? I'm currently using "radeonhd", which makes GE very slow.

---

### Post by ssri on 2009-05-18
Even though amd/ati released documentation for the R500 series (Mobility Radeon x2300 = Rv575) over a year ago, opensource 3D acceleration is still not to snuff.  This is not criticism for the opensource devs, rather criticism for amd/ati's decision to relegate 1.5-2yr cards to legacy status before the opensource drivers begin to approach feature parity with the 3D acceleration stack of the closed source fglrx drivers.  That being said, if you are dying to use google earth, then you should _downgrade to intrepid_ and _install catalyst 9.3_ or replace xserver 1.6 in jaunty with a custom built xserver 1.5.2 package and use catalyst 9.3 there.  Then again, using xserver 1.5.2 in jaunty may bring more instability in the system.

---

### Post by Arup on 2009-05-18
Before doing all this, have you tried turning off compiz and also turning off atmosphere in GE view?

---

### Post by haba7 on 2009-05-18
See [http://ati.cchtml.com/show_bug.cgi?id=1556#c5](http://ati.cchtml.com/show_bug.cgi?id=1556#c5)

I had some problems with DRI, but now everything is pretty much ok.

---

