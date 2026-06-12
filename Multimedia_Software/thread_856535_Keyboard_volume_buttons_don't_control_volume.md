---
title: "Keyboard volume buttons don't control volume"
date: 2008-07-11
forum: Multimedia Software
---

### Post by vbman11 on 2008-07-11
So this is probably not what you think.  My keyboard shortcuts do work, but not correctly. See when I press volume up the big speaker symbol pops up and it changes the little volume bar below it, but not the actual volume. Even If I turn the volume all the way down with my keys It is no different then with it al the way up. And the little volume control Icon near the clock works, but the big one doesn't. I'm going to try uninstalling pulse audio to see if that fixes anything. Any other suggestions?

---

### Post by dagoss on 2008-08-05
I have this exact same problem.  I suspect that the volume control on my keyboard is adjusting the volume for my onboard sound, rather than then SB Live! card I'm using, but I don't know enough to know if that makes any sense.

---

### Post by kostkon on 2008-08-05
You have to go to *System -> Preferences -> Sound*, select the first tab (*Devices*) and in the *Default Mixer Tracks* section select your sound card from the *Device* drop-down menu. Below it, you can define which volume level you want your keyboard volume keys to control.

---

### Post by vbman11 on 2008-08-07
Thanks but I just switched to intrepid and now I'm trying to get my volume keys to do anything, but that's for another topic.:)

---

### Post by beefcurry on 2009-04-18
Thanks :)

I had this on my Dell XPS M1330, it turned out the devices section was set to ALSA and not Pulse, on Jaunty, switching it to pulse solves it perfectly, but I sense skype problems coming.

---

