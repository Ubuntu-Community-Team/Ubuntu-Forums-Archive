---
title: "When ever I run Jack sound on everything else breaks."
date: 2013-02-22
forum: Multimedia Software
---

### Post by gravysteak on 2013-02-22
Hi I'm on xubuntu.
When ever I run Jack sound on everything else breaks. I'm using Rakarrack so I think I need to use it.

A restart fixes it but is there a way to turn off Jack and re-enable Pulse Audio from command line?

I tried.
```
jack_control stop
killall pulseaudio
pulseaudio
```
But still no sound. Actually when using gmusic browser when i tried to play a file before it would just lock up. 
After entering those commands it plays the file and the Pulse gui is reporting playback but no sound out of speakers.

---

### Post by luctor on 2013-02-22
try killall jackd
and/or killall jackdbus

qjackctl is a nice gui to manage jack
You might wanna add the kxstudio ppa's for awesome audio/multimedia stuff. They have a very good app called cadence that manages jack/alsa/pulseaudio stuff

[https://launchpad.net/~kxstudio-team/+archive/ppa](https://launchpad.net/~kxstudio-team/+archive/ppa)

[http://kxstudio.sourceforge.net/](http://kxstudio.sourceforge.net/)

---

### Post by gravysteak on 2013-02-22
Thanks
killall jackd fixes it without any other commands.

---

