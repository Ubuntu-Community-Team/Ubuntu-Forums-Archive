---
title: "Focusrite Saffire and Ubuntu 12.10"
date: 2013-03-21
forum: Multimedia Software
---

### Post by junglistric on 2013-03-21
This firewire interface is very unstable in Ubuntu 12.10.  Here is the error message that QJACKCTL gives as soon as I execute GNOME Mplayer:

Wed Mar 20 22:25:57 2013: [1m[31mERROR: JackFFADODriver::ffado_driver_wait - unhandled xrun[0m
Wed Mar 20 22:25:57 2013: [1m[31mERROR: firewire ERR: wait status < 0! (= -1)[0m
Wed Mar 20 22:25:57 2013: [1m[31mERROR: JackAudioDriver::ProcessAsync: read error, stopping...[0m
Wed Mar 20 22:25:57 2013: Jack: JackPosixThread::ThreadHandler : exit

This happens most of the time.  Sometimes, when I change settings in QJACKCTL and reboot, GNOME Mplayer runs fine (i'm trying to tweak settings such as sample rate, frames, etc).

For now I just want the interface to be stable, and to use GNOME Mplayer to play mp3s.  Is this too much to ask?

---

### Post by junglistric on 2013-03-21
OK, I got it to work this time by running jackd from command line before running qjackctl.  We will see if this is a permanent fix.

---

### Post by junglistric on 2013-03-21
I had also gotten Banshee to work, but after a reboot, same error:

[COLOR=#000000]Wed Mar 20 22:25:57 2013: [1m[31mERROR: JackFFADODriver::ffado_driver_wait - unhandled xrun[0m[/COLOR]
[COLOR=#000000]Wed Mar 20 22:25:57 2013: [1m[31mERROR: firewire ERR: wait status < 0! (= -1)[0m[/COLOR]
[COLOR=#000000]Wed Mar 20 22:25:57 2013: [1m[31mERROR: JackAudioDriver:[/COLOR]:razz:[COLOR=#000000]rocessAsync: read error, stopping...[0m[/COLOR]
[COLOR=#000000]Wed Mar 20 22:25:57 2013: Jack: JackPosixThread::ThreadHandler : exit

leads me to think this is something to do with the firmware or circuitry of the firewire device itself.  Is it not resetting properly?  Is there a memory cache in the firewire device?[/COLOR]

---

