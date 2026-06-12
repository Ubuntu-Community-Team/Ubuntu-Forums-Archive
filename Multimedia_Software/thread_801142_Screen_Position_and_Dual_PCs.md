---
title: "Screen Position and Dual PCs"
date: 2008-05-20
forum: Multimedia Software
---

### Post by satbunny on 2008-05-20
I have two PCs. Both share the same monitor through a KVM switch.
One runs Ubuntu 7.10 and Gnome and one runs Xubuntu 7.10 and XCFE.
One has a recent (8 series) NVIDA cardm and the other has a very old NVIDIA card. Both use the restricted driver that ships with Ubuntu.
I reinstalled and forgot to backup my xorg.conf.
Now one PC or another is generating an image which is 33% too far to the left or the right.
Previously I fixed this with a custom modeline.

Problem is I can't remember (or find on here) the right app to generate the custom modeline, and also I wonder of this is still the right way to do it or if there is something in the nvidia settings that can do it? [EDIT: I have tried xvidtune, but it fails saying "You have requested a modeline that is not possible or not supported by your hardware configuration."]

I would appreciate any advice on reminding me on how to do this..

---

### Post by satbunny on 2008-05-21
Bump

---

### Post by aeiah on 2008-05-21
i intermittently have this problem on my 7.10 xubuntu installation that i use for movies in the bedroom. its using an old nvidia FX card (5200?). the only way i got it to display properly was to fiddle with the resolution, changing it to something smaller and then back to native res, and then it started to display properly. once displayed properly, i just told xubuntu to save the session as is, and i havent seen the problem reoccur.

modelines are confusing. ive found the easiest thing to do is to export a custom modeline from powerstrip, a windows application. i doubt it will run in wine, but if you dual boot, you should be able to use this. you can copy settings to the clipboard and it usefully does this in a linux modeline format.

your modeline will be largely dependant on your monitor, so its pretty much a custom thing.

does this occur with both your computers? if so, have you tried setting the 'ignore EDID' flag in xorg.conf? perhaps your monitor is telling your computers the wrong information.

---

