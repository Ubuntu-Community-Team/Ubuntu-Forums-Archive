---
title: "Resolution different from what it says/how to force rez"
date: 2008-12-09
forum: Multimedia Software
---

### Post by vaasnaad on 2008-12-09
I have a Dell Dimension with an Intel 84X chipset onboard video and a Cornea CT1704 monitor (seems to use the same specs as a Benq model when I've messed with configuring), Ubuntu Hardy (because Intrepid won't even go to desktop outside safe graphics mode - my goal is to get Hardy going and then upgrade).  Ubuntu says it's running 1280x780 resolution, but it isn't.  It's running 1024x768 60HZ (that's what the monitor says its running), but it is somehow displaying all squished up as if it were 1280x780.  I've manually put in the monitor settings to the xorg.conf file and defaulted to 1280x1024 (the resolution I want to run), but when Ubuntu restarts, it says there's a problem and it is running in low graphics mode, and any time I put in the correct specifications, that's pretty much the end of it - I have to go in and restore to the original xorg.conf to get X to start again and get me to Gnome.

I've always had to manually tweak the xorg.conf file because of this monitor in Freespire, but any other distro I've used has actual specs in the xorg.conf file and not just "configured device" like Ubuntu does, and it doesn't like it when I manually tweak that like I've found instructions for.

Ubuntu is using a generic VESA driver - but seems to have hardware OpenGL acceleration?????  And a generic monitor (Configured Monitor in xorg.conf).  I have my monitor specs - is there anywhere in the Gnome GUI I can do to force it to use the setting I want?

---

### Post by overdrank on 2008-12-09
Hi and have you tried using the command ```
gksu displayconfig-gtk
``` and adjusting there.
If this fails you can always boot into recovery mode and use the xfix option to correct graphics issues.

---

### Post by vaasnaad on 2008-12-14
THAT DID IT!  Thanks a million, now it's all perfect!

---

