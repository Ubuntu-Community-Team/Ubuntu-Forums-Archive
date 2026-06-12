---
title: "Multimedia Volume Control Keys"
date: 2007-07-19
forum: Multimedia &amp; Video
---

### Post by djrobthaman on 2007-07-19
Hi Eveyrone,

I have discovered something that isn't really serious, but is pretty curious.  I have a keyboard with buttons for volume up/down/mute.  And when I press these buttons I see something pop up that shows the current volume of the system (or it thinks it does) and this pop up responds correctly to whatever button I press, but the system remains unchanged.

So, if I hit the mute button, the pop up shows that the system is muted but at the same time my amarok or whatever is playing keeps pumping full volume through the speakers.

Anybody know how to fix this?  Upgrade alsa maybe?

Thanks

---

### Post by wolfen69 on 2007-07-19
on my keyboard i have various multimedia keys that do not work or not as intended. even in windows you need a driver cd to get full functionality for keyboards to work correctly. i shrug it off.

---

### Post by djrobthaman on 2007-07-19
Yeah... like you say it's no big deal.  I just thought it strange because I'm sure it worked out of the box on previous installs (I've installed feisty a few times).  The previous installs were for the 64 bit architecture though and the one i'm using now is the regular version (only way I could get rid of the white cube of death), so maybe 64 bit ubuntu has something this one doesn't?

Oh well.

---

### Post by djrobthaman on 2007-07-23
Hi again,

I just figured out why the keys won't work but don't know how to fix it.  I was messing around with the alsa mixer on and realizes that when I use the multimedia keys the front mic volume gets changed.  Does anyone know how to switch the channel that the keys affect to the speakers?

Thanks

---

### Post by w1cked on 2007-12-06
I had the same issue using my Dell PowerEdge SC420. Ubuntu 7.10 Gutsy

Solution? System > Pref > Sound ... Choose your "default mixer track" (I got mine to adjust my vvolume properly with 'Analog Front')

---

### Post by SAndresen on 2007-12-06
Is PCM selected under System > Preferences > Sound? Is it set to the right Device?

---

