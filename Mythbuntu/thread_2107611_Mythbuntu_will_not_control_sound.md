---
title: "Mythbuntu will not control sound?"
date: 2013-01-22
forum: Mythbuntu
---

### Post by drewdin on 2013-01-22
I just built a frontend and I had an issue where the sound initially didn't work. I had to modify the tv setting and select the correct audio device, only one worked. I had to select nvidia dev=0 dmix. The only probvlem is that now my remote controo volume buttons and mute do not work. If i open the audio settings in the control panel, it will work.

My question is, has anyone else experienced this? How do I link the two different controls? I dont have a nvidia audio card so I dont know why its using my videocard as an audio source.

---

### Post by wyliecoyoteuk on 2013-01-22
are you using hdmi?

also, check the mixer settings

---

### Post by drewdin on 2013-01-22
unfortunately due to TV restrictions I am using S-Video and the green audio output jack on the back of my PC.

I checked the mixer and enabled speakers and audio control but no reaction from MythTV. I can adjust the volume and hit mute and see it wok on the screen but it does not effect the sound at all.

---

### Post by drewdin on 2013-01-25
anything? no one else have this issue?

---

### Post by km782 on 2013-01-29
> **drewdin said:**
> anything? no one else have this issue?

I have the same issue and unfortunately have just learned to live with it.  Whenever I need to mute or change the volume I just use the remote for my tv instead.  I'm sure that's not the answer you wanted to hear so if anyone has any suggestions I'd love to hear them.  The sound for my system is via HDMI.

---

### Post by drewdin on 2013-01-29
using ASLA:default I am able to get some sound using the remote but its very low. I have to turn the TV up so loud it hums. 

So i have the volume on the TV half way and I listen using the Mixer at max and using the remove volume at roughly 80%.

If i find anything else out ill post it here.

pretty much run aplay -L and see what audio devices you have on your system, cycle through them until you find one that works...

---

