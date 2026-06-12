---
title: "Pulse Audio not accepting connections ?"
date: 2009-11-05
forum: Multimedia Software
---

### Post by wwsoft on 2009-11-05
Hello , I cannot run [espeak]("http://espeak.sourceforge.net/") (from the command line or desktop), for some reason even with pulse audio running it reports this error

> ~$ espeak
>
> ~$ bt_audio_service_open: connect() failed: Connection refused (111)
> ~$ bt_audio_service_open: connect() failed: Connection refused (111)
> ~$ bt_audio_service_open: connect() failed: Connection refused (111)
> ~$  bt_audio_service_open: connect() failed: Connection refused (111)

I would like to fix this so feel free to give a suggestion ;)

---

### Post by sgx on 2009-11-05
I just discovered libpulse was secretly installed by mplayer, as a result, using wine to run vst DAW/vst-host apps Reaper and Cantabile
failed to work. Using synaptic to remove libpulse instantly solved
the problem. The pulse audio code should be removed from linux until it
is proved to be safe and stable.

---

