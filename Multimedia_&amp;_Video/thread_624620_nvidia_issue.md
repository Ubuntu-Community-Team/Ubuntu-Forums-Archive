---
title: "nvidia issue"
date: 2007-11-27
forum: Multimedia &amp; Video
---

### Post by Zipp0 on 2007-11-27
I installed the driver perfectly fine, the splash screen pops up, etc...but now on all my windows the toolbar doesn't show where you can minimize an application and crap...ANyone know what this problem is?

---

### Post by Znort_Ubern00b on 2007-11-27
I had similar problem and this worked for me.

open terminal and paste this in it:


sudo nvidia-xconfig --add-argb-glx-visuals -d 24

---

### Post by Zipp0 on 2007-11-27
I'll try that but terminal is popping up as just a white window. I can right click and it gives me the options to open a new tab and paste but I can't see squat.

---

### Post by Znort_Ubern00b on 2007-11-27
dunno about that...new one to me.

if it allows you to paste do so press enter, then type your password, press enter, and try reboot see if it works.

---

### Post by Zipp0 on 2007-11-27
Haha I rebooted now everythings fine...Thanks though!

---

