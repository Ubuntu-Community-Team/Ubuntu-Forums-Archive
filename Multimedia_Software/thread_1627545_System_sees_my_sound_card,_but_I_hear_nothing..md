---
title: "System sees my sound card, but I hear nothing."
date: 2010-11-21
forum: Multimedia Software
---

### Post by abelundercity on 2010-11-21
I was messing around with my audio settings last night and I think I did something that I shouldn't oughtta done.  Now, while my system can see my sound card, I'm hearing no output from it.  Pulseaudio volume control shows that it's hearing microphone input and it's playing Rhythmbox output.  I'm just not hearing it.

Has anyone encountered a problem like this and hit upon a solution?  Alternatively, is there a method through which I can chuck out all audio functions and reinstall fresh?

---

### Post by ajgreeny on 2010-11-21
In the sound preferences dialog from clicking the volume icon on your panel, go to the Hardware tab and choose different hardware in the bottom dropdown box.  That may be the problem.

If that's no help run *alsamixer* in terminal and check that the levels of outputs are not set too low or muted somewhere.

Move from slider to slider, and raise and lower levels with the cursor keys;
Mute and unmute with the "M" key.
Tab will move you from "playback" to "capture".
Esc will save and exit.

---

### Post by abelundercity on 2010-11-21
OK, did all of that, no joy.  Muting and unmuting the Master and PCM channels in alsamixer did produce a slight click, so there's life in there somewhere, I take it.

Nothing in sound preferences is muted, and volume levels are up.  I do note that under applications it's citing two distinct instances of the alsa plugin for Chrome (my current browser).  Don't know if that's significant.

(edit) Also, I've noticed that visualizations in VLC and Rhythmbox have slowed down to a real kludge, though video performance seems unaffected in other areas (DVD playback and 3D acceleration run just fine).  Again, I'm not certain what details are significant and what are not, but I thought it best to try to note anything anomalous.

---

