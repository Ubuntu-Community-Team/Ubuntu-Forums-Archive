---
title: "xrandr in sctip vs &quot;rotate&quot; in xorg.conf"
date: 2013-06-15
forum: Multimedia Software
---

### Post by r_avital on 2013-06-15
Hello all,

[If this is not the correct forum for this question, please redirect me.  Thanks!]

_**USING UBUNTU 10.04**_

I'm using a swivle monitor, and I'm trying to figure out the most effective strategy for rotating the X video output selectively, when I need to, depending on the application I use.

For years, I've had the following in the "Device" section in my xorg.conf:

```

Option    "Rotate"    "CCW"
Option    "RandRRotation"    "on"

```

This works fine, but to be more precise:  I get the Ubuntu Gnome ***Login screen in portrait*** (vertical), as well as all other windows in all other applications (with the monitor oriented vertically of course).  Everything is happy, except whenever I install almost anything from apt-get, synaptic, or update-manager, I now and then see messages on the console such as:
```
Xlib:  extension "RANDR" missing on display ":0.0".
RandR extension missing
```

This is fine, it does not impede installations of updates.

But if I want to temporarily rotate the display to a different orientation, I know I should be able to use a command such as: xrandr -o normal

And I get the same error.  I also noticed that if I launch Nvidia's proprietary configuration tool, there is no "Rotation" option available, even though my xorg.conf file clearly indicates "RandRRotation" "on"  -- and this happens ***regardless of whether*** "RandRRotation" "on"*** is above or below*** "rotate" "CCW"

***HOWEVER...***

If I remove the line "ROTATE"  "CCW"  -- THEN what happens:

[LIST=1]
[*]Login screen is always landscape (horizontal) 
[*]After login, the window is still landscape, until I change it. 
[*]I can change it, because both the RANDR extension is available (I can use xrandr -o left) AND the rotation option is available in the Nvidia configuration app. 
[/LIST]

Question:  

1. Are "Rotate" in xorg.conf and RANDR extension mutually exclusive?  If so, is that documented somewhere?  I could not find it in the X man pages.
2. Is it somehow possible to have the login screen in Portrait mode*** and still have the RANDR extension available***, to be able to run xrandr commands?

Thanks in advance!

---

### Post by r_avital on 2013-06-16
Okay, answered my own question.

1. Yes, the "rotate" option in xorg.conf is not compatible with the RANDR extension.  RANDR is supported as of X.Org version X11R6.8.1.  I found a clear statement to that effect in [ftp://download.nvidia.com/XFree86/Linux-x86/169.12/README/appendix-b.html](ftp://download.nvidia.com/XFree86/Linux-x86/169.12/README/appendix-b.html) -- I doubt that this is unique to Nvidia, but I could not find any similar statement in any of the "pure" xorg archives.

2. Found a fairly trivial solution, looking at my /etc/gdm/ folder, there are four folders: Init, PostLogin, PostSession, and PreSession.  Each has a script named "Default" (except PostLogin which has a script named "Default.Sample").

I edited /etc/gdm/init/Default -- the very last line reads: exit 0
Inserted just before that line: xrandr -o left

Now my login screen is output in portrait mode, and so is the post-login session, and the RANDR extension is available -- the "rotation" option in the Nvidia config screen is available, and xrandr commands in a terminal execute without errors.

---

