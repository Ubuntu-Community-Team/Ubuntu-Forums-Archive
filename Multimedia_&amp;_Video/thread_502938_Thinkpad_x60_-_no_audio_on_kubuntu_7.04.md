---
title: "Thinkpad x60 - no audio on kubuntu 7.04"
date: 2007-07-17
forum: Multimedia &amp; Video
---

### Post by l_tenhunen on 2007-07-17
Hello,

I recently installed Kubuntu 7.04 on my Thinkpad x60 laptop, which uses  AD1981HD chipset. As the topic tells I am having audio problems, and I am rather new with linux so don't be afraid to keep it simple stupid ;) Here's what I have tried after reading various guides and existing topics:

-Re-enabled my modem from Bios
-Topped volumes at Kmix for Master/Pcm/Micboost under Output tab, and also for Cd/Mic/Mic boost/capture under Input t-I haven't modified alsaconfig file (unless my old man did something to it whilst I was gone, however I think it's still intact).

That's about what I can remember.
Any help is appreciated!ab.
-Selected PCM as IEC958 Playback source under Switches tab.
-Shuffled mute button on laptop on and off and tested sound :)
-aplay -l lists the following:

"**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
 Subdevices: 0/1
 Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
 Subdevices: 1/1
 Subdevice #0: subdevice #0"

That's about everything I tried before I found the [comprehensive ubuntuforums audio guide]("http://ubuntuforums.org/showthread.php?t=205449"). After reading it, I tried the following:

- Checked that everything was unmuted in alsamixer (started from step 1).
- Installed alsa packages from fresh kernel with the following commands:
* sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
* sudo apt-get install linux-sound-base alsa-base alsa-utils

None of this has not solved my problem, so I am grateful for any assistance \\:D/
Cheers,

-lt

---

