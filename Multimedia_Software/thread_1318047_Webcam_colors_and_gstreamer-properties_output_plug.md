---
title: "Webcam colors and gstreamer-properties output plugin"
date: 2009-11-07
forum: Multimedia Software
---

### Post by Zaff on 2009-11-07
Hi everyone,
I upgraded to Karmic last night and everything seems fine except for one thing.
I noticed my webcam's colors in skype and cheese were "wrong" (I was blue, white was yellow, etc...), but not in kopete. So I went in gstreamer-properties and it turns out the problem is with the output plugin. If I select Autodetect or X Window System (X11/XShm/Xv) then the colors are weird, but if I select X Window System (No Xv) then they're fine again.

Now this fixes things in cheese and I'm guessing in all gnome apps, but not in skype. There are no options in skype to tell it what output plugin to use so I was wondering if there was an other solution.

Thanks for your help.

Edit : It turns out all you need to do is go in Totem Movie player, Edit -> Preferences -> Display and set the Hue to the middle (or click Reset to Default).

---

