---
title: "ati x800 gto2, ibex, openGL, waaaaah!"
date: 2008-11-20
forum: Multimedia Software
---

### Post by pietimer on 2008-11-20
Anyway, I just upgraded to Ibex, I have an x800gto2, and I want to get drivers working. Can anyone point me to a good tutorial or just tell me the secret?

I tried installing restricted drivers following [this]("http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide"). However, something is wrong with my drivers. fglrxinfo, glxgears, etc. all give:
> 
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  158 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  10
  Current serial number in output stream:  10


I uninstalled & reinstalled the drivers, typed glxgears, and it worked. Then I restarted and I'm getting that freakin' message again. Waaah! All I want in a cube desktop!

---

### Post by CHaoSlayeR on 2008-12-04
Hi pietimer,

have a look at this howto: [Setup FGLRX for compiz-fusion]("http://forum.compiz-fusion.org/showthread.php?t=6794")

This howto helped me a lot. Also please check your /var/log/Xorg.0.log for errors and warnings regarding to DRI 
, AIGLX and/or DRI. In addition the output of glxinfo, dmesg and/or xvinfo miay be helpful.

Greetz,

C]-[aoZ

---

