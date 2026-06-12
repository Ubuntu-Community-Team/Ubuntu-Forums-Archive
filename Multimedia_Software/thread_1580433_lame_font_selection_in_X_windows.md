---
title: "lame font selection in X windows"
date: 2010-09-23
forum: Multimedia Software
---

### Post by robertbub on 2010-09-23
I've been struggling with X11/Xfree86/xfonts fonts for a few days now.  Here are my problems.
[LIST=1]
[*]**Missing fonts.**  On my karmic machine, I get "freemono" when doing xlsfonts.  On my lucid and karmic running Xvnc, "freemono" is nowhere to be found.
[*]**Scaled fonts.**  On all machines, there are a number of fonts which have cannot be selected through *xfontsel* because the pixel size I desire is not available.  (When I used "-scaled", it is available, but, when I stick that font in my .Xdefaults file, it cannot be used.)
[/LIST]
I tried *fc-cache -fv*, but no more fonts appear.  I have the following packages installed:
[LIST][*]xfonts-100dpi
[*]xfonts-75dpi
[*]xfonts-base
[*]xfonts-encodings
[*]xfonts-mathml
[*]xfonts-scalable
[*]xfonts-utils
[/LIST]
Is there a guide or some magic sequence to fill-in omitted fonts and get a better font size selection?

My current workaround seems to be to default to "Courier" which is OK, but not the greatest.

(BTW, the fonts available through gtk/gnome is just fine.  Thankfully.)

---

