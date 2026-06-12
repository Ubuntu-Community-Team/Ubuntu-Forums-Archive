---
title: "Volume jumps up and down on boot of HP dv4 laptop"
date: 2010-08-22
forum: Multimedia Software
---

### Post by v1nsai on 2010-08-22
I'm working on a laptop for a friend who has decided to let me put Ubuntu on his computer to try it out along with his old Windows 7.  I've got Ubuntu up and running but every time I boot, the volume control goes nuts for about 30 seconds, jumping up and down from mute to full volume and back and forth.  

While this is happening, Xorg is using around 50% processor.  It's not a big deal and everything works fine when it's done, but it doesn't make the system look very stable to a newcomer :-/

Anyone have any idea of a way to stop this?  Like maybe I could pkill the volume manager process or something (what's it called?).  Any suggestions appreciated?

---

### Post by saporito on 2010-09-25
*bump*

I am having the same issue. Not on boot though. I used to have it on boot but now it is only when I use certain software (i.e. usually games, mupen64, boxee). You lose control of your computer.

---

### Post by saporito on 2010-09-25
I even tried to disable the sound card. No success. And the process you are thinking of is pulseaudio. As soon as you kill the process it starts back up :/. I am pretty sure it is not hardware because I am fine in windows

---

### Post by saporito on 2010-09-25
I have been doing some research and you're problem could be caused by static build up. Try rubbing the touch sensors several times to discharge static build up before boot. My problem = still unsolved

---

### Post by monstara on 2010-10-27
Hi, I have a Pavillion DV3, and experience the same issue, usually in games. Very mysterious. I thought it might be static, but touching the volume strip does not help.
Keycodes reported by 'showkey' for the strip are 114 (going down) and 115 (going up).
It's quite annoying, and it seems to sometimes toggle my wireless as well (the wireless key is next to the volume strip).

---

