---
title: "nxserver shadowing and gdm-2.28"
date: 2009-12-14
forum: Networking &amp; Wireless
---

### Post by resanders on 2009-12-14
Ubuntu 9.10 uses gdm-2.28 by default.  This has made it impossible for me to shadow Ubuntu 9.10 systems using nxclient.  In the shadow dialog to choose a display, the user is indicated as root rather than an actual user.  Logging in fails because of this.  It has been suggested to downgrade to gdm-2.20.  This does work, but I've found it can lead to problems booting some systems, and I would rather not go that route.  Does anyone know of any other solutions?  Is work being done on gdm-2.28 that would solve this problem?

For the time being, I've found using xdm a viable solution.  It has not given me any of the problems I encountered when using gdm-2.20 in Ubuntu 9.10.  

Thanks for any help.

---

### Post by resanders on 2009-12-16
I'm replying to my own post since some may find it useful, and I also have other information.

My main purpose of using the shadow option of nxclient is to give online help to others I am helping with their Ubuntu installations.  For the time being, the latest version of gdm and the nxserver software appear to not work well together.  I've found that changing the host computer (the one running nxserver) to xdm solves the login problem.  I found, however, that my screen would not refresh with any changes made on the host system.  Compiz running appears to be the culprit in that case.  So, by disabling compiz, I now can work at the host computer as if I'm sitting in front of the machine.  The easiest way I've found of disabling compiz is through a compiz-switch available for download.  The host user clicks the switch once to turn off compiz allowing my full access to his system.  After we've completed our work, the user then re-enables compiz by clicking the switch again. The compiz-switch can be found here:

[http://forlong.blogage.de/entries/pages/Compiz-Switch](http://forlong.blogage.de/entries/pages/Compiz-Switch)

---

