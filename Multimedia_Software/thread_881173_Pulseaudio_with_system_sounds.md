---
title: "Pulseaudio with system sounds"
date: 2008-08-05
forum: Multimedia Software
---

### Post by jeffchuck on 2008-08-05
I have pulseaudio streaming all of my audio to another machine, but I can't seem to get it to work with the system sounds.

In sound preferences, I set all of the devices to pulseaudio, and the Test buttons work with streaming the sound over the network, but when I go to the "sounds" tab and click play, the sound comes from my local speakers.

I've also tried install the ALSA plugin for pulseaudio and set all of the devices to ALSA with the same results.

Any ideas?

Thanks.

---

### Post by markbuntu on 2008-08-05
Open the Pulseudio Volume Control and see if the sound shows up there in Playback. It is probably playing on the wrong output device, or you have the wrong one set to default in the Output Devices section.

---

### Post by jeffchuck on 2008-08-07
No, it doesn't show up in volume control.

I only have one output device, and all of my devices in sound preferences are set to pulseaudio.

Is this a lost cause?  My only hypothesis is that the system sounds talk straight to the hardware at a level that skips the sound server.

---

### Post by markbuntu on 2008-08-07
Have you tried looking here:

[http://pulseaudio.org/wiki/FAQ](http://pulseaudio.org/wiki/FAQ)

I think there is some discussion about system sounds and some module you need loaded to play them. You can also try these:

[http://pulseaudio.org/wiki/Modules](http://pulseaudio.org/wiki/Modules)

[http://pulseaudio.org/wiki/PerfectSetup](http://pulseaudio.org/wiki/PerfectSetup)

---

