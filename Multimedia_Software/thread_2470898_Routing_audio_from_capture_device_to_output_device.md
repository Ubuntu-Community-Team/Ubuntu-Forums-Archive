---
title: "Routing audio from capture device to output device"
date: 2022-01-15
forum: Multimedia Software
---

### Post by spookybathtub on 2022-01-15
Hello.  I don't have much experience with linux audio and I'm trying to learn how to use ALSA and Jack.  My goal is to route audio from an AES67 virtual capture device to another AES67 virtual output device.  It seems like this can be done with Jack but I'm not sure I understand the process.  I'm on Ubuntu 20.04 headless with no X server, but I can use QJackCTL through SSH X11 forwarding.

Without Jack running, I verified the 8 channel input works:
```
arecord -Dhw:RAVENNA -c 8 -r 48000 -d 5 test.wav
```

Then I verified the output works and I can hear it on my AES67 receiver:
```
speaker-test -Dhw:RAVENNA -c 8 -r 48000
```

Then I used QJackCTL to patch system inputs 1-8 to system outputs 1-8.  But this way I don't hear any output.  I'm probably misunderstanding something about how Jack is supposed to work.  I set it to use the interface called hw:RAVENNA.  But how do I tell it to connect the "system" inputs and outputs to the actual sound interface (I would say hardware but it's virtual)?

---

