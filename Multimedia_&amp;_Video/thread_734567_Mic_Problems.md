---
title: "Mic Problems"
date: 2008-03-24
forum: Multimedia &amp; Video
---

### Post by patsissons on 2008-03-24
Kubuntu Fiesty running on an Asus A8N32-SLi Deluxe mobo, using the onboard sound (ac97).

the problem: alsa doesn't seem to accept input from the mic.  If i unmute my mic i can hear what i say into it on my speakers, so the signal is hitting the mobo and getting routed to the speakers.  But when i try to use it with any apps they do not hear anything.  I have tried to use it with both skype and arecord, both see that there is a mic connected, but refuse to record anything that comes in on it.  Any thoughts?

```
**** List of CAPTURE Hardware Devices ****
card 0: CK804 [NVidia CK804], device 0: Intel ICH [NVidia CK804]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CK804 [NVidia CK804], device 1: Intel ICH - MIC ADC [NVidia CK804 - MIC ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

---

### Post by BennBuntu on 2008-03-25
You've prolly tried this, most of my sound problems are fixed
with alsamixer in the terminal. Gives volume control for all channels.

---

