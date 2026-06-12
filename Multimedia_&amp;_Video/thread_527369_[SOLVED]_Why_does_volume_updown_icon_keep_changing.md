---
title: "[SOLVED] Why does volume up/down icon keep changing?"
date: 2007-08-16
forum: Multimedia &amp; Video
---

### Post by digitalbenji on 2007-08-16
Hi,
  I have a laptop that has a volume control external on it.  when I push up/down the volume pops up in ubuntu and goes up/down.  For a while it was a pretty MAC style big white icon w/ some transparency.  I liked it a lot.  Now suddenly it is a dinky little default volume meter.  What gives?  How do I get the good one back?

It's a system76 laptop btw.

Thanks,

---

### Post by DatsyukRules on 2007-08-17
I'm actually in the opposite situation.  I dont like the mac sound meter...its too big.  But I cant figure out how to change it.  

Any help would be appreciated.

---

### Post by digitalbenji on 2007-08-17
too bad we can't trade.  I'm sure someone will know about this.  Do you also have a system76 laptop?  If so, maybe we should move the thread/pull in system76 forums?

---

### Post by DatsyukRules on 2007-08-18
I have a dell inspiron 6000.

---

### Post by RomeReactor on 2007-08-18
HI. I think you're both referring to the sound icon with Desktop Effects enabled (first attachment) and the one without the effects (second attachment). Also, if you boot Ubuntu without the effects enabled, move sound up or down (so the small icon shows up) and **then** enable the effects, the small icon will remain; you then have to restart the X server for the big, transparent white volume icon to show (by pressing CTRL+ALT+BACKSPACE). Or by leaving the effects on and rebooting.

The opposite happens if you have the effects enabled and then disable them: the white transparent icon remains, but is opaque and looks gray. Restarting the X server or rebooting will change it to the small icon.

---

