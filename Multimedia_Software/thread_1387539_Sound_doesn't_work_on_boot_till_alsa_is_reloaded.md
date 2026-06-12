---
title: "Sound doesn't work on boot till alsa is reloaded"
date: 2010-01-22
forum: Multimedia Software
---

### Post by lgp171188 on 2010-01-22
I have been experiencing this peculiar issue with Ubuntu 9.10. Whenever the system boots, the audio doesn't work but when I do a 'sudo alsa force-reload', the volume icon gets muted and on unmuting it the audio works. This is the information regarding the audio device I get on doing lspci

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

Any ideas what could be causing this issue and how to resolve this?

---

### Post by VertexPusher on 2010-01-22
I have the same issue occasionally. My computer has three ALSA devices (onboard soundcard, webcam microphone, MIDI interface). Usually the onboard card is card 0 and the webcam mic is card 1, but sometimes the order is mixed up, and then I have to run "sudo alsa force-reload" to make sound work.

Do you have more than one ALSA device? You can check this by running "aplay -l" and "arecord -l" and "amidi -l".

---

### Post by lgp171188 on 2010-01-22
> **VertexPusher said:**
> I have the same issue occasionally. My computer has three ALSA devices (onboard soundcard, webcam microphone, MIDI interface). Usually the onboard card is card 0 and the webcam mic is card 1, but sometimes the order is mixed up, and then I have to run "sudo alsa force-reload" to make sound work.

Do you have more than one ALSA device? You can check this by running "aplay -l" and "arecord -l" and "amidi -l".
This is what I get when I do aplay -l

```

guru@guru-laptop:/etc/init.d$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC268 Analog [ALC268 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


```

My question is why am I having the same card number for my sound card and the Modem?
And is this causing the problem? How to rectify it?

---

### Post by VertexPusher on 2010-01-22
> **lgp171188 said:**
> This is what I get when I do aplay -l
Looks normal. Is this the result before or after reloading ALSA?

> My question is why am I having the same card number for my sound card and the Modem?Because the modem is part of the sound card.

> And is this causing the problem?No, unless PulseAudio somehow mistakes device 6 for device 0. But that would be a PulseAudio bug, not an ALSA bug. It's perfectly normal for ALSA cards to have several devices and subdevices. In a pure ALSA setup (i.e. without PulseAudio), the first device of the first soundcard will be selected as the default playback and recording device for all applications.

---

### Post by lgp171188 on 2010-01-22
Before alsa reload, immediately after boot, this is what aplay -l shows
```

card 0: Intel [HDA Intel], device 0: ALC268 Analog [ALC268 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

```

I can see that now Modem is listed as Subdevices: 0/1 instead 1/1 which was the output after force-reloading alsa.

---

### Post by josvanr on 2010-01-22
I've also been having this probelm since this morning (not after update??) but I did change the output volume yesterday in 'sound preferences' Now if I reboot there is no sound until 'alsa force-reload'..

---

### Post by VertexPusher on 2010-01-22
> **lgp171188 said:**
> I can see that now Modem is listed as Subdevices: 0/1 instead 1/1 which was the output after force-reloading alsa.
Interesting. I'll take a closer look at my aplay output when the problem occurs again. I always blamed the card renumbering, but you have only one card, so maybe there's a bug in ALSA or the HDA driver that causes the subdevice initialization to fail.

Can you disable the modem in your BIOS setup? Maybe that is sufficient as a workaround until the bug is fixed.

---

### Post by lgp171188 on 2011-09-14
> **VertexPusher said:**
> Interesting. I'll take a closer look at my aplay output when the problem occurs again. I always blamed the card renumbering, but you have only one card, so maybe there's a bug in ALSA or the HDA driver that causes the subdevice initialization to fail.

Can you disable the modem in your BIOS setup? Maybe that is sufficient as a workaround until the bug is fixed.
This issue is no longer reproducible in recent versions of Ubuntu that I have upgraded to. Hence marking this as solved. Thanks.

---

