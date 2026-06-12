---
title: "Microphone not working"
date: 2011-10-29
forum: Multimedia Software
---

### Post by pjtatlow on 2011-10-29
So I first discovered this problem when trying to make a Skype call for the first time. I went into Skype's options, and under "Sound devices" it told me that everything was controlled by PulseAudio. Okay, fine. So I went into Pulse Audio, and under Input Devices is listed Internal Audio Analog Stereo. But this will record no sound.I've tried all three port options (Analog Line-In, Analog Microphone, and Internal Microphone) and none of them will pick up any sound. I'm running Ubuntu alongside Windows 7, and the microphone works fine there. I have a Dell Studio XPS with an ATI High Definition Audio Device.

---

### Post by little_penguin on 2011-10-31
What kind of microphone are you using, could you tell us the make and model and also which version of Ubuntu you are running? Is the microphone USB, or one that plugs into the audio jack? I don't remember having to go directly into any Pulse Audio settings, all I did when setting up my microphone for Skype was to go to System Settings -> Sound -> Input. Just in case, check that nothing is accidentally muted.

---

### Post by bilderbuchi on 2011-11-08
This seems to be a bug: [https://bugs.launchpad.net/ubuntu/+source/skype/+bug/883404](https://bugs.launchpad.net/ubuntu/+source/skype/+bug/883404)

---

