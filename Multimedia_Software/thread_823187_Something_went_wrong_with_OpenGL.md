---
title: "Something went wrong with OpenGL"
date: 2008-06-09
forum: Multimedia Software
---

### Post by Master-of-None on 2008-06-09
Alright, something definitly went wrong here. Ever since I enabled Compiz Fusion(its disabled now) and installed Screenlets(its uninstalled now) Something VERY wrong has been going on with the graphics on my machine. Everything runs VERY slowly. IT lags like heck on anything slightly graphicly demanding. WINE can't run any windows programs because it can't render any of the programs fast enough for them to be useful.

Can you tell me what might be the problem? I have my ATI driver installed, so its not that. My OpenGL is up to date. What could be missing? Do you think my video card is broken? Its integrated graphics.

Whenever I try to change screen resolution, I get this message:

"The X Server does not support XRandR extension, Runtime resolution changes to the display size are not available"

Any help?

---

### Post by 16777216 on 2008-06-09
Paste the contents of the /etc/X11/xorg.conf file, and any backups or variations of it that are in the same directory.

If your graphics were going fine before turning on compiz it may have triggered a driver switch or a xorg.conf change that is not doing well for you.

---

