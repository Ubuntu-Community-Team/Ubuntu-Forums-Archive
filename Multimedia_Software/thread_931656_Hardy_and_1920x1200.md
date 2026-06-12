---
title: "Hardy and 1920x1200"
date: 2008-09-27
forum: Multimedia Software
---

### Post by n3kf on 2008-09-27
Hope someone can help sort this out. I recently came into possession of a samsung 243t. Anyway, this monitor works fine in (shudder) Windows XP at 1920x1200. In Hardy it also works fine at 1920x1200 using the standard ATI open source driver. When I go to the ATI fglrx driver, the best resolution I can get is 1600x1200. I have added 1920x1200 to the xorg.conf, changed the monitor to this using displayconfig.gtk, etc. Nothing seems to work. Interestingly when I go into display settings, the standard ATI driver knows this is a samsung monitor, but going to the same place with the fglrx driver it says unknown monitor. So is there any way to get to 1920x1200 using the fglrx driver, or is this a known limitation? I have only tried using the fglrx driver that is downloaded by Ubuntu if you want to turn on 3d. I have not tried the one from the ATI site (I do not know how recent the Ubuntu one is). Anyway, I believe the problem is that fglrx does not know what hardware it is on even though I think I did all I need to to tell it. Any other ideas how to get this to work? Thanks...

---

### Post by n3kf on 2008-09-27
I guess I should mention that the video card is an embedded Radeon Xpress 1250. Yes I know this would probably be a moot point if I was using and Nvidea adapter!!!!:(

---

### Post by markbuntu on 2008-09-27
You should file a bug report with ati. The devs need to know about things like this so they can fix them.

---

### Post by n3kf on 2008-09-28
Bump. So that is it? Everyone agrees that this is a bug. Does anyone else have a 24 inch widescreen working at 1920x1200? So how does one file a bug against the flgrx ATI driver?

---

### Post by markbuntu on 2008-09-28
Did you use the detect monitors option in the Catalyst Control Center?
If you did and it still did not correctly identify your monitor then file a bug report.

File your bug here or in Launchpad:

[http://ati.cchtml.com/](http://ati.cchtml.com/)

---

### Post by n3kf on 2008-10-01
Did not know about catalyst control center. When I run it the control center just calls it the default monitor. When I detect it, nothing happens. Interestingly enough, when I display the monitor information it says max resolution is 1920x1200 and max refresh is 75Hz. Both are correct. However, the part that lets you set the resolution and monitor only lets you select a max of 1600x1200 and 60Hz. Guess it is a bug.

---

