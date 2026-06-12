---
title: "VT1708BCE - microphone non-working"
date: 2011-12-25
forum: Multimedia Software
---

### Post by sm0ggy on 2011-12-25
Hello everyone!

I've got some problems with my microphone.
When i tried the live-cd from Ubuntu 11.10 the microphone works perfect.
But now after the install it does'nt!

i tried serveral things to figure out what it can be but i dont get it. 

Ofcourse i've run alsamixer and this gnome-interface for audio-settings. But it doesnt help.

This is something else what i've tried: [http://excid3.com/blog/changing-the-ubuntu-10-04-audio-channel-control/](http://excid3.com/blog/changing-the-ubuntu-10-04-audio-channel-control/)

Okey, after all i boot again the live-cd and run alsa-info.sh
Here is the result: [http://www.alsa-project.org/db/?f=a442f959d3b3a6e851b3cc9887c13babc4af1ed0](http://www.alsa-project.org/db/?f=a442f959d3b3a6e851b3cc9887c13babc4af1ed0)

and this one is from my installed Ubuntu: [http://www.alsa-project.org/db/?f=3afc5fa50159844542eb2f3ad80ff1fa7e33df12](http://www.alsa-project.org/db/?f=3afc5fa50159844542eb2f3ad80ff1fa7e33df12)

I hope you have anything you need. But if I forget something just let me know.

Greets from wounderfull Berlin!

//EDIT

I've solve the problem -.- smart5.1 was enabled what seems to block the microphone. *shame on me!*

---

### Post by inobe on 2011-12-25
smog, have you checked the simpler things before following howto articles?

alsamixer in terminal, see what's muted or turned all the way down.

have you install pavucontrol and looked at whats muted or turned all the way down.

what application do you need the mic for?

---

