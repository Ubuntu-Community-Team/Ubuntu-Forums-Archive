---
title: "VIA Epia diskless frontend doesn't work after upgrading to 10.04"
date: 2010-06-01
forum: Mythbuntu
---

### Post by freerkkalsbeek on 2010-06-01
Hi all,

I've upgraded the backend to Lucid and therefore created a new diskless image.
Unfortunately it doesn't work anymore. My Xserver segfaults.

I use a VIA Epia diskless frontend. The X driver loaded is the unichrome-pro driver.
Anyone else with the same problem?

Freerk

---

### Post by jack1323 on 2010-06-07
I also have a diskless Via frontend.  I'm running 9.10.  I think you've just scared me from upgrading.  Please post a reply if you fix the problem.

---

### Post by tgalati4 on 2010-06-07
If you can ssh into the box or from a console, look in /var/log/Xorg.0.log for errors and also look at .xsession-errors in your home directory.

cat /var/log/Xorg.0.log
cat ~/.xsession-errors

---

