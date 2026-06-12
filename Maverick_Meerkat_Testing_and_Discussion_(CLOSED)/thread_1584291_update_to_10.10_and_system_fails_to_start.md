---
title: "update to 10.10 and system fails to start"
date: 2010-09-28
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by tchoklat on 2010-09-28
I have run 10.4 happily under Parallels Desktop 6 on my iMac. I just ran a dist-upgrade to 10.10 beta and all went wrong.

Update worked fine. On reboot I get a message "an error occurred while mounting /media/psf" with options to skip mounting or manually fix it. To skip mounting puts me at a "tony-desktop login:" prompt and I do not know what to do, though if I log in as me and enter my password I get a message welcoming me to Ubuntu Maverick and a ~$ prompt Don't know what to do here. If I enter "startx" I get a fatal error - no screens ! And back to the ~$ prompt.

To manually fix it drops me also to a login prompt.

Tony

---

### Post by sdowney717 on 2010-09-29
when I first upgraded to MM I had a similar issue. Dumped me at a login prompt.
I managed to boot the gui using an earlier kernel.
I think my problem was related to the nvidia driver.

---

