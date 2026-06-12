---
title: "Mythtv loses sound if I run firefox"
date: 2013-01-19
forum: Mythbuntu
---

### Post by cedyathome on 2013-01-19
If I play a flash video (youtube, dailyshow etc) in firefox and pause it, and move to mythtv & try to play a recording, I get no sound. That's to be expected, but if I go back and exit firefox, I still get so sound out of mythtv. I need to go to Mythtv front end setup and scan for audio devices and then it works. Or reload the front end.

How do I configure Mythtv front end to avoid this or is there some other change that I need to make?

I have a work-around. Make sure to exit the page using audio on firefox before trying to play a mythtv recording, but I forget often & have to go through the scan rigmarole (or reload the front end). Not having a keyboard attached to the system makes this a pain.

Mythbuntu 11.10 and I update it regularly.

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: VT1708B Analog [VT1708B Analog]
  Subdevices: 1/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: NVidia [HDA NVidia], device 1: VT1708B Digital [VT1708B Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

I use this /etc/asound.conf
pcm.!default {
     type plug slave.pcm {
           type hw card 0 device 3
     }
}

There is no pulseaudio installed on the system.

Thank you.

---

### Post by cedyathome on 2013-01-19
I seemed to have found another solution, but don't really understand why it works.

In the mythtv frontend audio setup, I was using
ALSA:HW:CARD=NVidia,DEV=3

Just clicking around, I used
ALSA:HDMI:CARD=NVidia,DEV=0

Now, it doesn't lose audio like before.

But HDMI is on device 3 according to aplay-l, so I have no idea why this is working.

Any insight?

---

