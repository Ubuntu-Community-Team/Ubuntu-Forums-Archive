---
title: "Forcing X11 as Default?"
date: 2009-05-08
forum: Multimedia Software
---

### Post by LoREZ on 2009-05-08
Is there anyway to force X to use X11 as the default output for the desktop?  

I ask, because sometimes when I click on a graphical element (like a button or icon) my screen goes blank momentarily.  The same thing used to happen inside my preferred video apps (VLC and Gnome Mplayer) and the bug stopped when I forced output through x11.  Also, there doesn't seem to be a control for this in Totem (unless I missed a config file or something) and changing this setting might help with similar problems in that app as well.

Any thoughts?

My Stats:
OS: Dual-boot Jaunty/Win7 RC
CPU: Athlon XP 3000
HDD: 250GB IDE WD Caviar 
Graphics: nVidia GeForce 7600GS
Mobo: Abit KV8 Pro
Memory: 1.5 GB DDR RAM
Monitors: HP w2207 22"/Samsung SyncMaster 206BW 20"

---

### Post by kerry_s on 2009-05-08
x is x11. 
are using compiz?

---

### Post by LoREZ on 2009-05-08
Yes.  I thought about that. I disabled compiz and the bug went away. Do you think I should try installing the 185 beta drivers?  I'm currently using 182.

On a related note, only some of my compiz plugins seem to work when it is active.  For instance, I get Expo and wobbly windows, but none of my animations work, with the exception of some minimization effects. I've gotten them all to work on my machine before, though, under Intrepid.  Seen that before?

---

### Post by kerry_s on 2009-05-08
i think you just need to fine tune the driver, there are options you can use. try googling your model.

---

### Post by LoREZ on 2009-05-08
You are probably right, as this is the result from running compiz-check:

```
 Distribution:          Ubuntu 9.04
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation G73 [GeForce 7600 GS] (rev a2)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

```

While running Intrepid, it failed this test.  I'm using 185 now, and it works better, but animations are still unusable.  Which settings are you describing?  Xconfig?  nVidia-settings?

---

### Post by 7CarPileUp on 2009-05-08
Hey,

I had the same trouble with my ATI-X1300 (dirt cheap, dont ask)
I found something in a forum that helped.


press ALT+F2

Then type "gstreamer-properties"

You can configure it to default to X11


I had to set mine to "X window system (noXV)" which was the only one that seemed not to have any trouble.
Hope that helps. But it has a test video function so you can see the settings results before you close out the window.
--

---

### Post by LoREZ on 2009-05-08
Thanks, both of you.  Those suggestions helped.  I'm getting more comfortable with this OS every day.

---

