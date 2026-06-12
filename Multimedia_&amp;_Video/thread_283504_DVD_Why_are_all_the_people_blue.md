---
title: "DVD: Why are all the people blue?"
date: 2006-10-24
forum: Multimedia &amp; Video
---

### Post by DavidJE13 on 2006-10-24
I'm trying to get a lot of things working at the moment, and one of them is playing DVDs. I've installed all the necessary codecs &c. and (some) DVDs will now play in Movie Player...

Except that all the people are blue.

I can change the hue by 180 deg. to make the people (roughly) the right colour, but when I do that the trees go purple and character's lips go yellow-orange.

I have dual monitors, both connected to the same ATI card, and get the same problem whichever I play the movie on. I read that someone else has a similar problem, but that it is confined to just one monitor.

Has anyone else seen this? How do I fix it?

---

### Post by DavidJE13 on 2006-10-29
More info: (a disguised bump since it's been a few days ;))

The same DVDs play fine when I use other programs in my windows partition. But I'd much prefer to have it working in ubuntu so that I can finally shake off windows for good.

Also, when I play the DVDs it jumps straight to the movie and has no menu (even when I try to jump to the menu) is this normal?

---

### Post by nalmeth on 2006-10-29
As for skipping the DVD menu, you are probably using totem-gstreamer correct (the totem that came installed)?
gstreamer does not yet support DVD menus. If you don't want to switch to totem-xine (simple as installing the package of the same name), you could use a DVD player like OGLE or xine-ui solely  for DVD.

And about the color problem, are you using ATI's proprietary driver? You could try switching back to the open ati driver, or installing another version of the ATI driver, it's probably at fault. 

Alternatively you could try a different video player which allows you to change the video out driver (-vo). 

Look at xine, mplayer, change the -vo from XV to X11, or try a different video driver for the ATI card, you might find a working solution.

---

### Post by DavidJE13 on 2006-10-30
Switching to totem-xine seems to have solved both problems - thank you :)


small point: It seems that the only way to use the main menus is with the mouse - using the keyboard (really a remote control which acts as a keyboard) left+right change the position in the movie and up+down do nothing.

Not so important, but would be nice to fix :)

---

