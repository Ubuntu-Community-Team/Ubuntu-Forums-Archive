---
title: "Indicator Applet volume control messing up Alsa levels"
date: 2010-07-12
forum: Multimedia Software
---

### Post by salimfadhley on 2010-07-12
Since I upgraded to Ubuntu 10.4 the volume control has become very bizarre. Instead of the smooth transition from quiet to loud, just three clicks of the volume slider are enough to go from inaudible to amp-destroying / deafening. 

I can see the reason why this is happening. If I watch the output of AlsaMixer while I tweak the volume control I can see that it changes more than just the master volume. 

As I change the volume control, PCM, Front, Surround and Center, ( and possibly a few other channels that I do not care about) change at the same time. No wonder it creates an exponential response when I crank up the volume, since it's like turning up four volume knobs concurrently. 

So that's what's going wrong... but how do I fix it? Is there a configuration file which determines which of the many mixer volume levels the Indicator Applet's volume control actually changes? 

This PC was upgraded from Ubuntu 9.10... I wonder if there's some mixed up settings that are confusing it. Perhaps I could simply revert to a standard configuration? Might that solve the problem?

---

### Post by lidex on 2010-07-14
This should do it.
> There are a few variables which control how PulseAudio  controls the volume. You can either edit /etc/pulse/default.pa (you'll have to be root to do that) to change the behavior for all users, or copy that file to ~/.pulse/default.pa and then edit that file, to change behavior for the current user only.

Open the file mentioned above. Find the row saying "load-module module-udev-detect" and change it to:

load-module module-udev-detect ignore_dB=1

To try your changes, restart PulseAudio with the following command:

killall pulseaudio

PulseAudio will then autospawn (restart itself).

You may find that the above workaround is insufficient, in which case you may configure PulseAudio to control only one mixer control, e.g., PCM (cf. alsamixer). Find the row saying "#load-module module-alsa-sink" and change it to:

load-module module-alsa-sink control=PCM

(remember to remove the # in the beginning of the row!) Optionally replace PCM with the mixer control you want PulseAudio to control.

You will then need to killall pulseaudio as above and allow the daemon to autospawn. 

---

