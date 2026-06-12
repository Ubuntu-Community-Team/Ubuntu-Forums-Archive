---
title: "Restoring audio through HDMI"
date: 2013-08-27
forum: Multimedia Software
---

### Post by Ranko Kohime on 2013-08-27
I've run into a minor problem.  When my laptop is set to output audio on the HDMI port, if the HDMI cable is disconnected before the audio is switched back to the internal speakers, HDMI output then goes silent when plugged back in, until a reboot/suspend-awaken cycle.

I've tried killing the pulseaudio server, I've tried "sudo alsa force-reload", and neither of these fix the issue.

Anyone know what suspend does that killing all of the audio servers does not?

---

