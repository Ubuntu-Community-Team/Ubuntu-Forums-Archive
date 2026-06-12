---
title: "Screensaver fade"
date: 2006-09-30
forum: Multimedia &amp; Video
---

### Post by CatKiller on 2006-09-30
I posted this in another thread, but it might be helpful to others here, too.

I had a minor irritation with the fade of gnome-screensaver. It would fade out really slowly, then flash back to the desktop briefly, and then the screensaver would kick in. It had been fine in Breezy, which used xscreensaver. Having read > The MIT-SCREEN-SAVER extension is junk.  Don’t use it.
 in **man xscreensaver**, and noticing that xscreensaver disabled this extension by default, I amended my xorg.conf file from ```
	Load	"extmod"
``` to ```
SubSection "extmod"
	Option	"omit MIT-SCREEN-SAVER"
EndSubSection
#	Load	"extmod"
``` and the irritation went away.

Hope this helps someone.

---

### Post by json684 on 2006-10-20
I have the same problem, but your solution did not work. I still have the flash at the end of fade. I am using xscreensaver though. If anyone can help me out, that would be great.

---

### Post by json684 on 2006-10-28
I have isolated the problem somewhat for me. If I have xfce's compositor enabled I get the flash after the fade, if I don't have it enabled, the fade out works wonderfully. If anyone has any ideas that would be wonderful.

---

