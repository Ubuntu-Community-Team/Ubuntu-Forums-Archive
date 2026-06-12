---
title: "Front panel audio doesn't disable back panel?!!?"
date: 2009-11-07
forum: Multimedia Software
---

### Post by jmadgin on 2009-11-07
I'm looking for help with my front panel audio in 9.10, though I had the same problem in 9.04, 8.10 and 8.04 on both of my computers (both different motherboards).

After setting up the hardware correctly on the motherboard eg. Headers, I have the problem that in Ubuntu plugging the front panel audio jacks in does not cancel out the back panel output. I have installed windows to check if it was a hardware problem but in windows the front panel seems to disable the back panel.

This is obviously quite an important feature of the sound setup. When I have my headphones plugged in to the fp I want to cancel the back, why would I want it playing on both??!

I've done much searching on the net about this problem and it seems quite a big bug in Ubuntu and no-one seems to have the answer!?

Please HELP!

---

### Post by jmadgin on 2009-11-10
Bump!

---

### Post by jmadgin on 2010-01-06
Bump!

---

### Post by markbuntu on 2010-01-06
There are some issues with jack sensing in the low level alsa hardware drivers. These are vey hardware specific problems so each mobo has a very specific solution. The alsa devs are trying very hard to get all this working but they could always use more bug reports since they do not have all possible hardware at hand to test and are somewhat dependent on users to point out problems that they may be unaware of. Many manufacturers give zero support to this effort and some are actively hostile.

So, you can file a bug report to the alsa developers or you can try asking on one of their IRC channels or mailing lists or try a google search for more immediate help.

I know this does not solve your problem immediately, I only hope that you can gain some understanding of the scope of the problem.

btw, if you find a solution please post back here and I will make sure it gets into some troubleshooting guides that will be helpful to others.

---

### Post by Neosano on 2010-01-06
Isn't it awesome? You can use 4 speakers :-]

---

