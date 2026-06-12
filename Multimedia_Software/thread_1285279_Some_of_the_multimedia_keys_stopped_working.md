---
title: "Some of the multimedia keys stopped working"
date: 2009-10-07
forum: Multimedia Software
---

### Post by Mjoln on 2009-10-07
I have multimedi abuttons on my keyboard to play/pause music, control volume, mute sound, etc.
All the buttons worked fine out of the box when I installed ubuntu, but then suddenly some time ago play/pause button and mute button stopped working. They're still correctly assigned in keyboard shortcuts section of control panel and xev recognises them right (XF86AudioPlay is play/pause button), but they're not doing anything. Volume control buttons and all the other extra buttons are working fine except play/pause and mute.

---

### Post by Mjoln on 2009-10-14
I noticed that if I make a custom key assignment for command "rhythmbox-client --play-pause" and assign it to any non-extra key on my keyboard, it works. But if I assign it to XF86AudioPlay, it doesn't work. Can someone tell me what package handles those multimediakeys so I can try reinstalling it or something. It's pretty weird that the particular play/pause button doesn't work even though xev recognises it correctly and the exact same command works if I assign it to any normal key.

---

