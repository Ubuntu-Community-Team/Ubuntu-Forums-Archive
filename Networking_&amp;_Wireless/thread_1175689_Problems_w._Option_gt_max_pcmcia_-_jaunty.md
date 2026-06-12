---
title: "Problems w. Option gt max pcmcia - jaunty"
date: 2009-06-01
forum: Networking &amp; Wireless
---

### Post by pippom77 on 2009-06-01
Hi! I'm a (happy!) newbye of Linux.

Recently I upgraded my Ubuntu version from HH to Jaunty Jackalope; before the upgrade I could connect to the Internet via my Option GT MAX 7.2 Ready PCMCIA card. The driver I had was nozomi (I never installed it: I found it "automatically").

With the new version of the OS this is no more possilbe and I can't understand why...
When I try to connect by clicking on the network manager near the clock it starts to seek the modem; after some seconds a messages inform me that the connection can't be estabilished.

I tried to install (by apt-get) gcom drivers but the error messages of "gcom" given on the bash says that "/dev/modem" directory can't be found (and naturally that directory doesn't exist...).
As regard Nozomi drivers, I can't find them: as already said, I found them already installed with the previous version of Ubuntu and I don't know where to look to get them (Synaptic doesn't give results for "nozomi"...).

Does anyone have some suggestion to help me?

Thank you!!!!

bye
Marco

---

### Post by pippom77 on 2009-06-05
I solved the problem (by myself!) this way. The correct procedure is the following:

-Insert the card after the boot, with system ready.

-In bash:   gcom -d ttyUSB0

-connect as usually

The procedure is a little annoying: I don't know if there's an alternative (automatic) way. I think this (the absence of the correct driver) is a bug in Jaunty... Nevertheless now I can netsurf...

Marco

---

### Post by Trevice on 2009-06-13
same problem here, I have to use "gcom -d ..blabla" whenever I boot. If someone knows an automatic way to connect at start plz...

by the way, I have an option globertroter UMTS card

---

