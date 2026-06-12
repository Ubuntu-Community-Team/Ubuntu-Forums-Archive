---
title: "Sound device using PulseAudio?"
date: 2010-03-13
forum: Multimedia Software
---

### Post by Thoddy on 2010-03-13
Hi, I installed "Theocracy" on my 9.10 Karmic system. The installer asks for a sound device, dev/dsp is the default and I didn't change it. When I now try to start the game, I get the following error:

Unable to open sound device: Device or resource busy
Aborted
Execution of /usr/games/theocracy_base/theocracy.real failed!

What is the sound device when using PulseAudio on Karmic?

Thanks!

---

### Post by Yellow Pasque on 2010-03-13
Based on the age of the game, it might only support OSS. You can try to use the padsp utility to make the application work.
```
sudo apt-get install pulseaudio-utils
padsp <command>
```
[http://pulseaudio.org/wiki/PerfectSetup#OSSApplications](http://pulseaudio.org/wiki/PerfectSetup#OSSApplications)

---

### Post by Thoddy on 2010-03-14
Thanks for the reply!

It seems that was some strange coincidence, however. Plus I already had that package installed.

This message only appears the first time I try to start the game. If I try to start it again I only get the the other two lines:


Aborted
Execution of /usr/games/theocracy_base/theocracy.real failed!


Seems to be a general of this game with new distributions!?

---

