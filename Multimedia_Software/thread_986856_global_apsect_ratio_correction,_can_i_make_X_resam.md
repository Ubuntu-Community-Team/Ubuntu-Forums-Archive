---
title: "global apsect ratio correction, can i make X resample my entire display?"
date: 2008-11-19
forum: Multimedia Software
---

### Post by ahumin on 2008-11-19
after a lot of headaches trying to get my laptop to use nvidia drivers and recognise my plasma tv, i have it working - kinda. i had to use [FONT="monospace"]envyng[/FONT] because the drivers available from synaptic and nvidia's site both failed miserably, and then i had to edit my [FONT="monospace"]xorg.conf[/FONT] file because the [FONT="monospace"]nvidia-settings[/FONT] tool failed to properly detect the tv.

the tv is connected with a vga cable, set as a separate X window. the maximum resolution it supports is 1024x768, but it's 16:9 so the output is horizontally stretched.

is there a way i can can trick ubuntu or X into thinking that it's a 1366x768 monitor then have some software layer resample the entire output to the right res for the tv? that would be much easier to use than fiddling around with aspect ratio corrections in individual programs, and gnome wouldn't be so fat either.

---

