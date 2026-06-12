---
title: "Winbind Install Issues"
date: 2010-09-24
forum: Networking &amp; Wireless
---

### Post by anhume on 2010-09-24
With both Ubuntu 8 and 10, first one, then the other,on a Sony laptop, I had installed winbind (as well as editing smb.conf) so as to access Windows boxes on a wireless network.  At first the install worked OK on the 8 system but then, on rebooting, it hung while trying to start the winbind daemon.  On the 10 system, after running apt-get install winbind, the procedure hung when trying to start the winbind daemon towards the end of the install process.  It looks like there is an error in the on-line winbind download code that was not there last month (I previously had several successful winbind installs) but it is there now.  Incidentally, what do I do when an install (from the terminal) hangs in this way?  Thanks for your help

---

### Post by capscrew on 2010-09-24
> **anhume said:**
> With both Ubuntu 8 and 10, first one, then the other,on a Sony laptop, I had installed winbind (as well as editing smb.conf) so as to access Windows boxes on a wireless network.  At first the install worked OK on the 8 system but then, on rebooting, it hung while trying to start the winbind daemon.  On the 10 system, after running apt-get install winbind, the procedure hung when trying to start the winbind daemon towards the end of the install process.  It looks like there is an error in the on-line winbind download code that was not there last month (I previously had several successful winbind installs) but it is there now.  Incidentally, what do I do when an install (from the terminal) hangs in this way?  Thanks for your help

Is this a AD domain setup?  Why do you feel you need Winbind?

---

