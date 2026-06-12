---
title: "color adjust on all xsessions"
date: 2007-02-10
forum: Multimedia &amp; Video
---

### Post by sleepercivic88 on 2007-02-10
I have a monitor where the color adjustment in the monitor does not adjust so im using nvidia-settings to do the adjustment for me

I made a ~/.xinitrc script that contains the following.

#!/usr/bin/env bash
nvidia-settings -l &
exec gnome-session


Im really new at scripting but I know java im not really sure if I need the &

the coloradjustment works when I stop gdm and startx

to have this normally execute at every start of gdm you usually link it to ~/.xsessions
"ln -s ~/.xinitrc ~/.xsessions

I dont have a .xsessions file so where do I link the file to

Im pretty new at this kind of stuff so sorry for my noobness.

---

### Post by sleepercivic88 on 2007-02-11
anyone?

---

