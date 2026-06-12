---
title: "Strange issue with Google Hangouts and Pulseaudio"
date: 2014-04-02
forum: Multimedia Software
---

### Post by obsidian razor on 2014-04-02
Hi everyone,

Lately I've been having a very odd issue with Google Hangouts. When I call a phone number through it, the sound starts extremely distorted. However, after a few seconds it usually stops and audio returns to normal, except when it doesn't, but there doesn't seem to be any pattern to it, most of the time (70% I'd say) it corrects itself in about 2 seconds, but the remainder of the time it doesn't go away.

I tried removing Pulseaudio from my system, as I've read that it causes a myriad of problems, and it must be the cause of this, since if I remove it, the problem goes away and Hangouts works fine with ALSA. Reinstalling Pulseaudio afterwards brings back the problem.

I cannot stay with ALSA for long though, as for some reason, it refuses to acknowledge my multimedia keys in this laptop (which is really odd) no matter how many times I try to re-stablish the shortcuts. 

Can anybody help? I don't even know where to begin.

---

### Post by dannyboy79 on 2014-04-04
i do have weird things going on with pulseaudio and for some strange reason just opening pavucontrol (the little speaker icon within Xubuntu 13.10) will make the issue go away. it's really unxplainable why opening an app would solve it. another thing that i've tried to solve it is within pavucontrol go to the configuration tab and turn off your sound output device and then turn it back on. that solves a weird issue with playback in audacity.

---

### Post by obsidian razor on 2014-04-04
Thanks!

I'll try it. At this point I need to find a way to make this work or go back to windows :(

---

