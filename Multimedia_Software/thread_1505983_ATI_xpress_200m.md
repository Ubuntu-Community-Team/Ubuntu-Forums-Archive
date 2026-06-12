---
title: "ATI xpress 200m"
date: 2010-06-09
forum: Multimedia Software
---

### Post by alliance1975 on 2010-06-09
I'm tracking/monitoring 2 bugs on launchpad, (574034 & 570879). Both address problems withxserver-xorg-video-ati and the xpress 200m video. I was wondering if a solution is found how is it usually announced and how long before it would appear in an update?

---

### Post by efflandt on 2010-06-10
Have you tried **nomodeset** (or **radeon.modeset=0**) kernel boot parameter to see if disabling kernel mode setting (kms) helps?

[https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Working%20around%20bugs%20in%20the%20new%20kernel%20video%20architecture](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Working%20around%20bugs%20in%20the%20new%20kernel%20video%20architecture)

I have a Compaq Presario V2000 with Radeon Express 200M.  I have not tried Google Earth on it.  But I was never able to suspend or hibernate in 9.10 (would not resume or wake), and I can now successfully suspend and resume in 10.04.  I used nomodeset just because glxgears ran a bit faster and I have had trouble with kms on other older ATI video chips.

---

### Post by alliance1975 on 2010-06-11
Thanks for your reply. However, I've switched back to 9.10 and do not wish to go thru the effort of reloading 10.04. I will wait and hope that something will be done on the bugs and that somehow it will be made available.

---

