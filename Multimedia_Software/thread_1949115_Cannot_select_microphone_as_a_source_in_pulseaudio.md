---
title: "Cannot select microphone as a source in pulseaudio"
date: 2012-03-29
forum: Multimedia Software
---

### Post by flatko on 2012-03-29
Hi there.
I have a strange issue in my Ubuntu 11.10 - I'm not able to record any sound from the microphone.
 If I choose Mic as a connector in "Sound settings", it doesnt change settings in alsamixer. If I change the setting manually in alsamxer, the "Sound settings" shows muted input. Unmuting it or sliding the input volume changes the source back to line-in ](*,) Line capture works well, but no way to set it to capture mic.

Anyway, using JACK, mic capture works with no problems. I need it to work in Pulseaudio in order to use Skype and Empathy.

---

### Post by flatko on 2012-03-30
Still nobody with the same issue? It's really an enigma ](*,)

---

### Post by Rodney9 on 2012-03-30
Try pavucontrol

sudo apt-get install pavucontrol

PulseAudio, previously known as Polypaudio, is a sound server for POSIX and WIN32 systems. It is a drop in replacement for the ESD sound server with much better latency, mixing/re-sampling quality and overall architecture.

PulseAudio Volume Control (pavucontrol) is a simple GTK+ based volume control tool (mixer) for the PulseAudio sound server. In contrast to classic mixer tools this one allows you to control both the volume of hardware devices and of each playback stream separately. It also allows you to redirect a playback stream to another output device without interrupting playback.


Rodney

---

### Post by flatko on 2012-03-30
Thank you, Rodney9, for the reply.

I just solved the problem by deleting ~/.pulse and ~/.pulse-cookie
I first tried it in Guest user and it worked, so I found that it was user-related issue in Pulseaudio.

Don't know why this can happen.

Edit: Switching back to line-in input messes things up again.

Multimedia audio controller: nVidia Corporation nForce3 250Gb AC'97 Audio Controller (rev a1)

---

