---
title: "mplayer ignores mouse"
date: 2009-05-03
forum: Multimedia Software
---

### Post by Cephi on 2009-05-03
I've added several lines like:
> MOUSE_BTN0 volume 1
to my input.conf.  I've tried altering that line with a variety of mouse buttons, and a variety of mplayer commands.  I can't get mplayer to recognize any mouse event.  I have read that mplayer is supposed to be hardcoded to seek in response to the scroll wheel; mine doesn't.  I've tried both my computer's trackpad and two different usb mice, all with the same (lack of) result.

I've checked to make sure that my config files don't include the line nomouseinput=1.  I've even tried adding the line nomouseinput=0.  Mplayer is accepting keyboard input just fine.

Any help would be much appreciated.  I'm at a dead end.

running 8.04 xubuntu on a 4G eee pc btw.

---

### Post by Cephi on 2009-05-03
New info: I now see that the above is true only for audio playback.  I can control video playback via the mouse.  How can I do so for audio playback as well?  Any ideas?

---

### Post by Cephi on 2009-05-04
Okay, well, I'm currently controlling my music via the mouse by slaving mplayer to a FIFO, then opening up an instance of vim with all the mouse buttons remapped so that pressing them writes various commands to the FIFO.  It does everything I need it to do.... but it's a pretty ugly hack.  Help would be appreciated.

---

