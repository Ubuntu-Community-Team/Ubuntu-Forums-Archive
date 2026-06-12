---
title: "Dual Screen with two separate desktops (not TwinView)"
date: 2007-06-26
forum: Multimedia &amp; Video
---

### Post by areks on 2007-06-26
Hi,

I'm trying to connect second monitor to my laptop using nvidia graphics card.
I did read [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_setup_Dual_Monitors_with_NVidia_in_Feisty_Fawn](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_setup_Dual_Monitors_with_NVidia_in_Feisty_Fawn)
Actually setting TwinView just work from from nvidia-settings and I don't need to set anything manually in xorg.conf

Unfortunately I found what TwinView is useless for me as screen size (ratio) at laptop and on second one are different. This resoult in part of the desktop being invisible. 
What I would like to achieve is two separate desktops (workspaces) displayed one on each sreen. I was trying to set "Separate X screen" but unfortunately nvidia-settings is not able to save changes. The error is:

```
ERROR: Unable to determine valid vertical refresh ranges for display device
       'CPT' (GPU: GeForce Go 7400)!
ERROR: Failed to add display device 'CPT' to screen 1!
ERROR: Failed to add X screen 1 to X config.
ERROR: Failed to add X screens to X config.
ERROR: Failed to generate an X config file!
```

This is happening also if I select manually settings for my laptop display (CPT).
Does anybody knows how to fix it or maybe how I should change xorg.conf myself?

Thank you

---

### Post by sargeras on 2007-06-26
I know you said "not twinview", but I thought I'd throw this out there....I am using twinview

I am not sure about your error, but in my Xorg.conf I have a line that says something like this:

MetaModes     "1600x1200, 1600x1200", "1600x1200, null"

Have you tried setting the two resolutions to the correct ones for your laptop and external monitor?  It should display them correctly then (no missing "desktop area")
Sorry I can't be more specific, but I am not at my ubuntu computer right now.

Hope this helps a little

---

### Post by areks on 2007-06-27
I replaced nvidia-glx with nvidia-glx-new and it is much better now. I can save X Configuration without problem.

Basically I can set it the way I would like it to be, but there is one small problem left, if I enable Xinerama I cannot start any terminal window :(

---

### Post by areks on 2007-06-27
It looks like this is know bug. It can be fixed by adding 

```
Section "Extensions"
Option "Composite" "false"
EndSection
```

to the end of xorg.conf

:D

See this post for more info: [http://ubuntuforums.org/showthread.php?t=485286&highlight=terminal+Xinerama](http://ubuntuforums.org/showthread.php?t=485286&highlight=terminal+Xinerama)

---

