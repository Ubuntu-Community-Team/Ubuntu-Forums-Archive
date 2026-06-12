---
title: "Compiz on xinerama dual head"
date: 2008-03-28
forum: Multimedia &amp; Video
---

### Post by boazarad on 2008-03-28
I'm using a dual head setup configured with nvidia-settings as seperate x servers in xinerama mode- I would like to have compiz runnning, even only on the main screen - can this be accomplished? how?

---

### Post by Yellow Pasque on 2008-03-28
My advice would be to wait for Hardy/8.04 to be released. That includes Compiz 0.7.2 which will support effects on multiple monitors.
> I would like to have compiz runnning, even only on the main screen - can this be accomplished?
It may be possible; I'm not sure. What output do you get from typing *compiz* in a terminal? Also, see this post for some basic tips on setting up compiz: [http://ubuntuforums.org/showpost.php?p=4202892&postcount=6](http://ubuntuforums.org/showpost.php?p=4202892&postcount=6)

---

### Post by boazarad on 2008-03-28
I'm running the hardy dev version - with compiz 0.7.2
While in xinerama mode compiz reports "no composite extention" - though the xorg log file clearly detects its presence :(

Here is my compiz version info - while in single screen mode with compiz running:
```
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0422 (rev a1) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1680x1050) to maximum 3D texture size (8192): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
compiz 0.7.2

```

---

### Post by boazarad on 2008-03-28
I was using xinerama beacuse twinview didn't seen to be handling maximizing correctly.
All it needed was a proper xorg.conf write from nvidia-settings, and an X restart.

Now I have compiz - and window maximization works properly!

---

