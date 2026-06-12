---
title: "Gnome / 10.04 -  Amarok kills audio in (mic) - need reboot"
date: 2010-11-27
forum: Multimedia Software
---

### Post by markthekdeguy on 2010-11-27
Here's one for the audio guru's out there. a standard Ubuntu 10.04 LTS fresh install, updated, Amarok 2.3.0 installed from Ubuntu software centre, skype 2.1.0.81, audio codec (HDA Intel) ATI ALC 272.. laptop

i noticed skype works ok. until Amarok is started.then, no audio *in* works until a reboot. its not just Skype. in Pavucontrol, audio in works, 'level in' meter flickers as normal on speech. start Amarok, wherever the level in meter was a second or two after amarok gets started, the meter reading 'freezes' - amarok plays,, no audio in can be obtained any way i can see, suggesting the fault may be Amarok locking pulseaudio input, up, just the input though. and closing amarok has no effect on the now 'dead' audio input. maybe a phonon / pulseaudio issue..
In Kubuntu 10.04 LTS i have to install Pulseaudio to get skype to send my mic audio out at correct 'speed' - otherwise i sound like i'm a 45 vinyl record played at 33 or slower. on Kubuntu without pulse, skype is unuseable. i have tried old skype's on Kubuntu, some give good in/out audio, without pulse installed, but crash on messages. something is wrong with some software. i am stuck. i have submitted several bug reports, and been trying to resolve this for nearly a year... compiled, tweaked, edited, reinstalled Kubuntu, Xubuntu Kubuntu. nothing.ALSA on some distros using KDE 3.5 it all works.
anyone help please ?

---

### Post by markthekdeguy on 2010-11-27
Bump   bring back ALSA / dmix

---

