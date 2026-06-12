---
title: "GNOME Sound Preferences default output device"
date: 2010-01-28
forum: Multimedia Software
---

### Post by cidolfas on 2010-01-28
Here's the situation:

I have Myth (and my entire system) working over HDMI 100%, both video and audio.  The only annoyance is that whenever the system boots I have to manually right click on the sound icon, open sound preferences, go to the output tab, and select the second option, "RS780 Azalia controller Digital Stereo (HDMI)", if I want the volume controls to work.  By default, the first entry is selected, "RS780 Azalia controller", and sound does play with it selected.  After I select the proper output entry, I can open the command line and start mythfrontend (it only outputs sound when opened from the command line, probably due to my use of EXPERIMENTALLY_ALLOW_PULSE_AUDIO as an environment variable) and everything works, including volume control from within Mythfrontend.

My question is this: is there some way to make the option that's second on the list (the one with "Digital Stereo (HDMI)") the default?  I don't want to change my setup, and I could only get sound to work using Pulse and forcing pulse to load my hardware.

Just for kicks, here my aplay -l:
```
alex@Hestia:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
```

---

