---
title: "Legacy ATI card owners using 9.04: There may be hope yet"
date: 2009-05-27
forum: Multimedia Software
---

### Post by Sand &amp; Mercury on 2009-05-27
Since I have been blessed with the wonderfully inadequate chipset Radeon Xpress200M, and with Ubuntu 9.04 ATI has so thoughtfully elected to add all users of this card over to the legacy driver effectively leaving me high and dry, I've been shopping around for alternatives. 

The OOTB Mesa driver was more or less an abortion for performance and stability, but the Radeon Rewrite driver which has been getting around lately has been improving things, I'm happy to say. Key things I noted:

[LIST]
[*]Frame rates are noticeably improved. Still nowhere close to the old fglrx, but beggars can't be choosers, I guess.
[*]X no longer crashes when exiting full screen OpenGL games.
[*]X no longer seems to freeze when trying to move OpenGL windows, but still leave horrible artefacts under Compiz.
[*]No more horrible visual glitches with dynamic lights in certain games.
[*]Trying Cooliris on Firefox still manages to cause a hard lock up.
[*]Scrolling in apps is still nice n' smooth, the one good thing I've seen come of the new Xorg in Jaunty.
[*]Performance in the following apps is still just as abominable as before: Google Earth, Source engine games in Steam, and Kwin with compositing on.
[/LIST]
If you're an owner of one of the newly abandoned ATI cards and are suffering a bit for it, I'd suggest giving the rewrite a shot. You can do so by adding the PPA here:

[https://launchpad.net/~xorg-edgers/+archive/radeon](https://launchpad.net/~xorg-edgers/+archive/radeon)

and then updating. They have instructions there in case something goes pear-shaped.

---

### Post by ssri on 2009-05-27
Thanks for the update, keep 'em coming :mrgreen:

---

### Post by imbjr on 2009-05-28
Damn. I hoped Google Earth was not going to suffer under Jaunty with my ATI X1300 card.

I installed it a week or so ago and have only now fired it up for a proper good session today - only to find it will not tolerate even its own dialogs overlaying the main display.

*shakes fist at ATI*

---

### Post by imbjr on 2009-05-28
> **imbjr said:**
> Damn. I hoped Google Earth was not going to suffer under Jaunty with my ATI X1300 card.

I installed it a week or so ago and have only now fired it up for a proper good session today - only to find it will not tolerate even its own dialogs overlaying the main display.

*shakes fist at ATI*

Just tried the RadeonHD driver again.

Pro: Google Earth behaves itself.
Cons: Runs slow. Screen resolution is not at its maximum; probably need to crack open xorg.conf and fiddle about.

So - back to using the default Radeon driver.

*shakes fist at ATI some moar*

---

### Post by imbjr on 2009-05-28
> **imbjr said:**
> Just tried the RadeonHD driver again.

Pro: Google Earth behaves itself.
Cons: Runs slow. Screen resolution is not at its maximum; probably need to crack open xorg.conf and fiddle about.

So - back to using the default Radeon driver.

*shakes fist at ATI some moar*

LOL

Just tried Google Earth again, back with the default Radeon driver, and its behaving itself much better. Still a little glitchy tho.

---

