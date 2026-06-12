---
title: "Ati &amp; Madwifi restricted modules"
date: 2006-07-25
forum: Multimedia &amp; Video
---

### Post by dtruesdale on 2006-07-25
Ok I think I have figured out why so many of us can't get the ati drivers working. We can't remove all the restricted modules or we lose our wireless. I have a Sage 8790 which has a 9600m and atheros wireless. I keep getting the  ati response of:

Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

If I remove the restricted modules i lose my wireless. I was looking for info on madwifi as it should be it's own module outside the restricted modules, even better yet why are they not all seperate so we can remove and plug in new ones without losing others? I have done everything under the wiki to the forums to figure this out and this seems to be the only answer I have. Anyone else have any sugestions or ideas?

---

### Post by whatever on 2006-07-25
you can blacklist the old fglrx module (included in restricted modules) in /etc/default/linux-restricted-modules-common like described in [this guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)...

---

### Post by dtruesdale on 2006-07-25
Did that and it still gives issues loading the new one from the link you provided. Something is not 100% here.

---

