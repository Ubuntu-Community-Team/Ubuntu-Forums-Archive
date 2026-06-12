---
title: "disabling pulseaudio"
date: 2010-07-06
forum: Multimedia Software
---

### Post by methodtwo on 2010-07-06
Hi
As i mentioned in my previous thread about sound, my sound wasn't working.I then did:
```
$rm -r .pulse
```
This didn't fix the problem.So i did:
```
$sudo apt-get install pulseaudio

```
It said that pulseaudio was allready at the latest version.When i looked in my home directory there was a .pulse directory there again.
I then uncommented the line in the pulseaudio client config, telling pulseaudio not to respawn once it had been killed.I then did:
```
$kill -9 pulseaudio_process_id.
```
This fixed the problem of there being no sound.I could hear things when i played them with flash etc.
However every time i boot the system pulseaudio doesn't get started.Also my system seems to be a bit unstable now:firefox crashed when flash was playing something, and the whole desktop and the mouse and keyboard locked.I had to reboot by shutting the power off at the wall.
I was wondering is my sound fix a safe one?.Is the unstable behaviour due to the fact that i've broken the system in my quest to get sound working?.Should i re-enable pulseaudio(how??)and look for a better fix to get the sound working?.Thank you for your time
regards

---

### Post by cherva on 2010-07-06
Pulse is configured to run on per user basis so in order to stop it from running every time you login open  /etc/pulse/client.conf 

```
gksu gedit /etc/pulse/client.conf
```
and change autospawn  to no
```
autospawn=no
```

---

### Post by methodtwo on 2010-07-06
That's exactly what i allready did(as mentioned at the start of this thread)

---

### Post by methodtwo on 2010-07-06
My question was:will this make my system unstable?.Thank you for your time
regards

---

### Post by cherva on 2010-07-06
If I were you ... I'd remove the pulseaudio package and reinstall ALSA.

---

