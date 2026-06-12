---
title: "Sound works for some things but not always others?"
date: 2008-08-11
forum: Multimedia Software
---

### Post by RB2610 on 2008-08-11
I have a 5.1 creative soundblaster live speaker set, with the appropriate sound card and Ubuntu recognises it, it even has an option for SB live 5.1 (Alsa mixer) in the sound options.
I use the SB live 5.1 Alsa mixer most of the time but I have also tried the default HDA Intel one sometimes.
The startup sound always works, so do all other system related sounds including sound previews in the File Browser, also music in Exaile, Amarok and Rythmbox always works. And sound in the games that come with Ubuntu (solitaire, mines and that kind of thing)
However,other sounds, anything in Firefox and the sound in games played through Wine only works sometimes and if it doesn't I need to restart (sometimes multiple times) to get it to work again.

Is there any way I can fix this problem?

---

### Post by scragar on 2008-08-11
problem is pulse audio.

[http://ubuntuforums.org/showthread.php?t=885437](http://ubuntuforums.org/showthread.php?t=885437)

or alternativly you can just add ```
killall pulseaudio
```
in for a startup ap(System>preferences>sessions).

choice is yours(I prefair my way, less work and easier to undo)

---

### Post by RB2610 on 2008-08-11
Thank you, so I just stick that in as the command and restart?

---

### Post by RB2610 on 2008-08-11
I tried it, no there is no sound :(

---

### Post by scragar on 2008-08-11
By no sound you mean no sound at all? or do you mean no change? if there's no sound at all restart pulseaudio and remove my fix(to restart it just press alt+F2, then type "pulseaudio" into the box, restart anything using sound), then follow the advice of the link I posted.

---

### Post by RB2610 on 2008-08-11
Ah, nevermind, I had only restarted the session (I wanted to avoid restarting as I have a problem with booting up atm which I'm trying to get sorted) but after a full restart everything seems to work (except system sounds but that doesn't really matter)

Thanks again :)

---

