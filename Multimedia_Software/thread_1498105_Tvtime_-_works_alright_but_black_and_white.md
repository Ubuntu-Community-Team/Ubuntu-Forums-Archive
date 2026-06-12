---
title: "Tvtime - works alright but black and white?"
date: 2010-05-31
forum: Multimedia Software
---

### Post by lugoteehalt on 2010-05-31
New install of the latest Ubuntu.  Put in Tvtime and it worked straight away, sound and video, (although does not seem to want to switch between svideo, television, and composite, at least nothing seems to happen.)

But it is in black and white!?  Tried right-click menus nothing obvious seems to change things.  Thanks any help.

---

### Post by WinterRain on 2010-05-31
I don't know about tvtime, but you could try [TV-Viewer]("http://sourceforge.net/projects/tv-viewer/"). Works good for me.

---

### Post by xc3RnbFO8P on 2010-05-31
> **lugoteehalt said:**
> New install of the latest Ubuntu.  Put in Tvtime and it worked straight away, sound and video, (although does not seem to want to switch between svideo, television, and composite, at least nothing seems to happen.)

But it is in black and white!?  Tried right-click menus nothing obvious seems to change things.  Thanks any help.

From TVtime site:[http://tvtime.sourceforge.net/problems.html#tvwonder]("http://tvtime.sourceforge.net/problems.html#tvwonder")
> 1. Channels black-and-white and numbers off-by-one

The tuner driver defaults to detecting a PAL tuner on many NTSC capture cards, a notable example being the ATI TV Wonder cards. This causes all of the cable frequencies to be out of alignment, channel numbers are off-by-one and slightly detuned. To fix this, the tuner type must be told explicitly when loading your capture driver. For example, with the bttv driver use the following:

    modprobe bttv tuner=2

You may have to first remove the bttv module if it is already loaded. To make this change automatic, in your /etc/modules.conf file, add the following line:

    options bttv tuner=2

This will ensure that whenever the tuner module is loaded, it will use the correct tuner for this card. If this does not fix the problem please post a bug report on the tvtime bugs page.

In older versions of bttv, this module option could also be passed to the tuner module. This method is deprecated in newer 2.6 kernels, and so you must pass the parameter to the capture driver itself.

To attack this problem, we believe that the tuner module must be fixed to correctly detect the difference in tuner, as so many users are affected by this problem. To help with this, please follow up on tvtime bug 711428.

---

